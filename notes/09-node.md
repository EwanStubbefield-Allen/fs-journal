# Node

<!-- SECTION Controller -->
  export class Controller extends OtherController { --> inherits code from another constructor
    constructor () {
      super('query') --> runs constructor from extended controller
      this.router --> enables following http requests
        .get('', this.getFunction)
        .get('/:id', this.getFunctionById)
        .use(Auth0Provider.getAuthorizedUserInfo) --> anything after requires authorization
        .post('', this.createFunction)
        .put('/:id', this.updateFunction)
        .delete('/:id', this.removeFunction)
    }
    async getFunction(req, res, next) {
      try {
        const data = await Service.getFunction()
        res.send(data)
      } catch (error) {
        next(error)
      }
    }
    async getFunctionById(req, res, next) {
      try {
        const data = await Service.getFunction(req.params.id)
        res.send(data)
      } catch (error) {
        next(error)
      }
    }
    async createFunction(req, res, next) {
      try {
        const variable = req.body
        variable.creatorId = req.userInfo.id
        const data = await Service.createFunction(variable)
        res.send(data)
      } catch (error) {
        next(error)
      }
    }
    async updateFunction(req, res, next) {
      try {
        const dataId = req.params.id
        const userId = req.userInfo.id
        const update = req.body
        const data = await Service.updateFunction(dataId, userId, update)
        res.send(data)
      } catch (error) {
        next(error)
      }
    }
    async removeFunction(req, res, next) {
      try {
        const dataId = req.params.id
        const userId = req.userInfo.id
        await Service.removeFunction(dataId, userId)
      } catch (error) {
        next(error)
      }
    }
  }

<!-- SECTION Service -->
  class Service {
    async getFunction() {
      const data = await dbContext.Collection.find()
      return data
    }
    async getFunctionById(id) {
      const data = await dbContext.Collection.findById(id)
      if (!data) {
        throw new BadRequest('message')
      }
      return data
    }
    async createFunction(data) {
      const variable = await dbContext.Collection.create(data)
      return variable
    }
    async updateFunction(dataId, userId, update) {
      const original = await this.getFunctionById(dataId)
      if (variable.creatorId.toString() != userId) {
        throw new Forbidden('message')
      }
      original.value = update.value || original.value
      await original.save()
      return original
    }
    async removeFunction(dataId, userId) {
      const variable = await this.getFunctionById(id)
      if (variable.creatorId.toString() != userId) {
        throw new Forbidden('message')
      }
      await variable.remove()
    }
  }

<!-- SECTION Database -->
  Register in dbContext:
    Collections = mongoose.model('Collection', nameSchema)

<!-- SECTION Model -->
  export const nameSchema = new Schema({
    property: { type: String, required: true, maxlength: , minlength: },
    property: { type: Number, max: , min: }
    property: { type: Boolean, default: false }
    property: { type: String, enum: [options] }
    creatorId: { type: Schema.type.ObjectId, required: true }
  }, { timestamps:true, toJSON: { virtuals: true } })
# Node

<!-- SECTION Database -->
  export const data = [
    {
      key: value
    }
  ]

<!-- SECTION Controller -->
  export Class Controller extends OtherController --> inherits code from another constructor
    constructor () {
      super('query') --> runs constructor from extended controller
      this.router 
      .get('additional query', this.getFunction)
      .get('/:id', this.getFunctionId)
      .post('', this.createFunction)
      .put('/:id', this.updateFunction)
      .delete('/:id', this.deleteFunction)
    }
    async getFunction(req, res, next) {
      try {
        const variable = await Service.getFunction()
        res.send(variable)
      } catch (error) {
        next(error)
      }
    }
    async getFunctionId(req, res, next) {
      try {
        const Id = req.params.id
        const variable = await Service.getFunctionId(Id)
        res.send(variable)
      } catch (error) {
        next(error)
      }
    }
    async createFunction(req, res, next) {
      try {
        const data = req.body
        const variable = await Service.createFunction(data)
      } catch (error) {
        next(error)
      }
    }
    async updateFunction(req, res, next) {
      try {
        const id = req.params.id
        const data = req.body
        const variable = await Service.updateFunction(id, data)
      } catch (error) {
        next(error)
      }
    }
    async deleteFunction(req, res, next) {
      try {
        const id = req.params.id
        await Service.deleteFunction(id)
      } catch (error) {
        next(error)
      }
    }
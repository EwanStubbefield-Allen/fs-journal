# Async

<!-- SECTION C.R.U.D. -->
  C --> create
  async create(data) {
    const res = await api.post('adds at end of base url', data)
    const newClass = new Class(res.data)
    AppState.variable.push(newClass)
    AppState.emit('variable')
  }

  R --> read
  async getApi() {
    const res = await api.get('adds at end of base url')
    AppState.variable = res.data.map(r => new Class(r))
    AppState.emit('variable')
  }

  U --> update
  async update(data, id) {
    const res = await api.put('adds at end of base url/${id}', data)
    const updated = new Class(res.data)
    const oldArrayIndex = array.findIndex(a => a.id == id)
    if(oldArrayIndex == -1) {
      throw new Error('error')
    } 
    array.splice(oldArrayIndex, 1, updated)
  }

  D --> delete
  async delete(id) {
    cons res = await api.delete('adds at end of base url/${id}')
    const arrayIndex = array.findIndex(a => a.id == id)
    if(arrayIndex == -1) {
      throw new Error('error')
    } 
    array.splice(arrayIndex, 1)
    AppState.emit('variable')
  }
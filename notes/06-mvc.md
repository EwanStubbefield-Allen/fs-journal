# MVC

View --> App --> Router --> Controller --> Service --> Models(AppState)
AppState --> Where all global variables are stored
Constructor --> Runs on class initialization
  AppState.on('variable', function) --> when variable changes run function
  AppState.emit('variable') --> manually activates the listener

<!-- SECTION Router -->
  Router --> Contains all controllers to be used from HTML
  export const router = [
    {
      path: `#/`,
      controller: ,
      view: `HTML`
    }
  ]

<!-- SECTION View -->
  View --> User interacts
  export const view = `HTML`

<!-- SECTION Controller -->
  Controller --> Dictates user abilities
  export class Controller {Methods}

<!-- SECTION Service --> 
  Service --> Modifies Models
  class Service {Methods}
  export const Service = new Service()

<!-- SECTION Model -->
  Models --> Tracks information
  export class Model {
    Constructor(data) {
      this.name = data.name
    }
    get template() {return}
    
    static get name() {return}
  }

<!-- SECTION Import/Export -->
  import { variables } from "./location.js"
  export type name() {}
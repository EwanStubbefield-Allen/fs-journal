# MVC

View --> App --> Router --> Controller --> Service --> Models(AppState)
View --> User interacts
Router --> Contains all controllers to be used from HTML
AppState --> Where all global variables are stored
Constructor --> Runs on class initialization
  AppState.on('variable', function) --> when variable changes run function
  AppState.emit('variable') --> manually activates the listener

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
    get template() {return `html`}
  }

<!-- SECTION Import/Export -->
  import { variables } from "./location.js"
  export type name() {}
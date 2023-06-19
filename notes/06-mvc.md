# MVC

View --> App --> Router --> Controller --> Service --> Models(AppState)
View --> User interacts
Router --> Contains all controllers to be used from HTML
AppState --> Where all global variables are stored
Controller --> Dictates user abilities
Service --> Modifies Models
Models --> Tracks information
Constructor --> Runs on class initialization

<!-- SECTION Import/Export -->
  import { variables } from "./location.js"
  export const variable = value
  export function function() {}

<!-- SECTION Classes -->
  export class name {
    constructor() {

    }

    methodName() {
      
    }
  }
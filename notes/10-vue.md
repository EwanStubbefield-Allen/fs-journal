# Vue

<!-- SECTION Pages -->
  HTML:
    @ = v-on
    @click="" --> Calls function on click
    v-for="variable in array" --> repeats code for each array variable
    v-if="conditional" --> only runs if conditional is true
    :key="variable.key" --> gives view a unique identifier for each variable (collin binds property)
    :class="{ 'key': conditional }" --> if conditional is true applies key to class
    :property="JavaScript" --> collin allows JavaScript
    {{ variable }} --> inject JavaScript variable into HTML

  JavaScript:
    setup() { --> Private variables/functions
      let variable = ref(value) --> Adds a listener and will update HTML (probably better to use reactive)
      return { --> public variables/functions
        newVariable: AppState.variable, --> gets variable from appState and can rename it
        newVariable: computed(() => { return AppState.variable }), --> Allows newVariable to be reactive
        newVariable.value --> Gets the variable value
      }
    }
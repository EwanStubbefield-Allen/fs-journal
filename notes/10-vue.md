# Vue

<!-- SECTION HTML -->
  V-:
    @ = v-on
      @click="function()" --> Calls function on click
      @submit="function()" --> Calls function on submit
      @submit.prevent="function()" --> Calls function on submit and prevents default
    v-if="conditional" --> only runs if conditional is true
    v-elseif="conditional" --> runs if conditional is true and all prior v-ifs are false
    v-else --> runs if all v-ifs are false
    v-show="conditional" --> is similar to v-if but only hides content
    v-model="object.variable" --> creates two way data binding
    v-for="variable in array" --> repeats code for each array variable
      :key="variable.key" --> gives view a unique identifier for each variable  
  :class="{ 'key': conditional }" --> if conditional is true applies key to class
  :attribute="JavaScript" --> collin allows JavaScript

  {{ variable }} --> inject JavaScript variable into HTML
  <Component :nameProp="variable"></Component> --> Calls component and gives a prop
  <router-link :to="{ name: 'Name', params: { id: variable } }"></router-link> --> Goes to said page when clicked on content and can append a param
  <slot name:"name"></slot> --> Takes HTML from the parent and inserts it
  <template #name></template> --> Specifies which slot 

<!-- SECTION JavaScript -->
  export default {
    props: {
      nameProp: { type: Type, required: bool } --> Defines prop that is passed from parent
    },
    setup(props) { --> Private variables/functions and passes props through
      let object = ref({}) --> Adds two way data binding
      const route = useRoute() --> Gets the route the user is on
      onMounted(() => {}) --> The constructor of view
      onUnmounted(() => {}) --> When page is closed
      watchEffect(() => {conditional}) --> Continuously checks to see if conditional is true
      return { --> public variables/functions
        newVariable: AppState.variable, --> gets variable from appState and can rename it
        newVariable: computed(() => { return AppState.variable }), --> Allows newVariable to be reactive
      }
      components: { Component }
    }
  }

<!-- SECTION Router -->
  const routes = {
    {
      path: '/name/:id'
      name: 'Name'
      component: loadPage('NamePage')
    }
  }
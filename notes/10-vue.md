# Vue

<!-- SECTION HTML -->
  V-:
    v-if="conditional" --> Only runs if conditional is true
      v-elseif="conditional" --> Runs if conditional is true and all prior v-ifs are false
      v-else --> Runs if all v-ifs are false
    v-show="conditional" --> Is similar to v-if but only hides content but keeps css
    v-model="object.variable" --> Creates two way data binding
    v-for="variable in array" --> Repeats code for each array variable
    @ = v-on
      @click="function()" --> Calls function on click
      @submit="function()" --> Calls function on submit
      @submit.prevent="function()" --> Calls function on submit and prevents default
    : = v-bind:
      :key="variable.key" --> Gives view a unique identifier for each variable used after v-for
      :class="{ 'key': conditional }" --> If conditional is true applies key to class
      :attribute="JavaScript" --> Collin allows JavaScript

  {{ variable }} --> Inject JavaScript variable into HTML
  <Component :nameProp="variable"></Component> --> Calls component and gives a prop
  <router-link :to="{ name: 'Name', params: { nameId: variable } }"></router-link> --> Goes to said page when clicked on content and can append a param
  <slot name:"name"></slot> --> Takes HTML from the parent and inserts it
  <template #name></template> --> Specifies which slot 

<!-- SECTION JavaScript -->
  export default {
    props: {
      nameProp: { type: Type, required: bool } --> Defines prop that is passed from parent
    },
    setup(props) { --> Private variables/functions and passes props through
      let object = ref({}) --> Adds two way data binding
      const route = useRoute() --> Gets the url the user is on
      const nameId = route.params.nameId --> Gets the params from the url
      onMounted(() => {}) --> The constructor of view
      onUnmounted(() => {}) --> When page is closed
      watchEffect(() => {Operation}) --> Continuously checks to see if a value inside changed and runs
      return { --> Public variables/functions
        newVariable: AppState.variable, --> Gets variable from appState and can rename it
        newVariable: computed(() => { return AppState.variable }), --> Allows newVariable to be reactive
      }
      components: { Component }
    }
  }

<!-- SECTION CSS -->
  v-bind(JavaScript) --> Allows Javascript in css however can't string interpolate in here

<!-- SECTION Router -->
  const routes = {
    {
      path: '/name/:id'
      name: 'Name'
      component: loadPage('NamePage')
    }
  }
# Observables

<!-- SECTION Backend sockets -->
  export class Name extends SocketHandler {
    constructor(io, socket) {
      super(io, socket, true) --> If true requires auth
      this
        .on('VARIABLE', this.function)
        .on('DIFFERENT-VARIABLE', this.toggleFunction)
    }
    function() {
      this.socket.emit(message) --> Sends back message when called
    }
    toggleFunction() {
      this.io.to('room').emit(message) --> Sends back message to users in the room when called
    }
  }

<!-- SECTION Frontend sockets -->
  class Name extends SocketHandler {
    constructor() {
      super(true) --> If true requires auth
      this.on('VARIABLE', this.function)
    }
    function(variable) { --> Variable is the message received from backend
    }
  }

  export const name = new Name()

  onMounted(() => {
    name.emit('VARIABLE', { message: 'string', values }) --> Sends request to backend
  })
# Observables

<!-- SECTION Frontend sockets -->
  class Name extends SocketHandler {
    constructor() {
      super(true) --> If true requires auth
      this.on('MESSAGE', this.function) --> Runs function when receiving said message
    }
    function(variable) { --> Variable is the message received from backend
    }
  }

  export const name = new Name()

  onMounted(() => {
    name.emit('MESSAGE', { message: 'string', values }) --> Sends request to backend

<!-- SECTION Backend sockets -->
  export class NameHandler extends SocketHandler {
    constructor(io, socket) {
      super(io, socket, true) --> If true requires auth
      this
        .on('MESSAGE', this.function)
        .on('DIFFERENT_MESSAGE', this.toggleFunction)
    }
    function() {
      this.socket.emit('MESSAGE') --> Sends back message when called
      this.socket.join('id') --> When called user joins room
      this.socket.leave('id') --> When called user leaves room
    }
    toggleFunction() {
      this.io.to('room').emit(message) --> Sends back message to users in the room when called
    }
  }
  })
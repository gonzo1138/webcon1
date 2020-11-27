<template>
  <div>
    <form id="cmd" v-on:submit.prevent>  <!-- alternativ: v-on:submit.prevent="readcmd">  -->
      $ <input id="cmdin" v-model="command" @keyup="readcmd($event)" placeholder="test" autofocus type="text" autocomplete="off" size="42"/>
    </form>
    <p>Command is: {{ prompt }}</p>
  </div>
</template>

<script>
  export default {
    name: "GlWebshell",
    data() {
      return {
        command: "",
        prompt: ""
      }
    },
    methods: {
      readcmd: function (event) {
        var befehle = {
          'print': function () {this.prompt = "Hello World"}
        }
        //this.prompt = befehle['print']; //befehle.get('print');
        //console.log("test"+event.keyCode);
        //this.prompt = event.code;
        //if (event.code === 'Enter') this.prompt = this.command;
        if (event.code === 'Enter') {
          //if (Object.keys(befehle).includes(this.command)) befehle.get(this.command);
          this.prompt = befehle[this.command];
        }
        //this.prompt = event.code;
        switch (this.command) {
          case "clear":
          case "test":
            this.prompt = this.command;
            break;
          case "exit":
          case "quit":

            break;
          default:
            break;
        }
      }
    }
  }
</script>

<style scoped>
  a{
    text-decoration: none;
    color: #0c0;
  }
  a:visited {
    background: #ccc1;
  }
  a:focus, a:hover, a:active{
    background: #ccc7;
  }

  .orders{
    display: none;
  }

  input{
    border: 0px;
    background-color: #00000000;
    font-family: Roboto-mono, monospace;
    color: #009000;
    font-size: medium;
    border: 0px;
    margin: 0px;
    outline: none;
  }

  table{
    width: 100%;
    border: 0;
  }

  .boxes{
    width: 100%;
  }

  #spacer{
    height: 200px;
  }

  #consolewindow{
    position: absolute;
    width: 699px;
    height: 400px;
    margin-left: 100px;


    background-color: #ccc1;
    transform-origin: left;
    transform: perspective(699px) rotateY(7deg);

  }

  #consoleheader{
    width: 100%;
    height: 34px;
    top: 0px;
    background-size: auto;
    background-position-y: 0px;
    background-repeat: no-repeat;
    background-color: #ccc1;
  }

  #consoleframe{
    width: 100%;
    height: 368px;
    background: #ccc0;
    position: absolute;
    bottom: 0px;
    display: flex;
    justify-content: flex-start;
    flex-direction: column;
    overflow-x: hidden;
    overflow-y: scroll;
  }

  #console{
    background: #ccc0;
  }

  #prompt{
    background:#ccc0;

  }
</style>
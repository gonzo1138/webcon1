<template>
  <div>
    <ul>
<!--      <li v-for="item in items" :key="item.message">
        {{ item.message }}
      </li>-->
      <li v-for="item in output" :key="item">
        {{ item }}
      </li>
    </ul>
    <!--<p ref="listing">{{ prompt }}</p>-->
    <form id="cmd" v-on:submit.prevent>  <!-- alternativ: v-on:submit.prevent="readcmd">  -->
      $ <input id="cmdin" v-model="command" @keyup="readcmd($event)" placeholder="test" autofocus type="text" autocomplete="off" size="42"/>
    </form>
  </div>
</template>

<script>
  export default {
    name: "GlWebshell",
    data() {
      return {
        command: "",
        prompt: "",
        items : [
          { message: 'Fooooooo' },
          { message: 'Bar' }
        ],
        output : [],
        history : []
      }
    },
    methods: {
      readcmd: function (event) {
        //var fx=function (){
        //  this.output.push("FX");
        //}
        function runfn(ctx, fn) {
          //console.log(fn);
          if (fn !== undefined){
            console.log(fn.name,'>',ctx);
            fn.bind(ctx)();
          }
          //parent.this.prompt = "scopeHello!";
          //ctx.prompt = "Hello!xxx";
          //var x = fn;
          //fn.bind(ctx);
          //fn();
          //alert("blub");
        }
        var befehle = {
          'printx': function printx() { alert("printx")},
          'clr'   : function clrname() { this.output.push("CLEAR");},
          'clrx'  : function () { this.output=[];}
        }
        //this.prompt = befehle['print']; //befehle.get('print');
        //console.log("test"+event.keyCode);
        //this.prompt = event.code;
        //if (event.code === 'Enter') this.prompt = this.command;
        if (event.code === 'Enter') {
          //if (Object.keys(befehle).includes(this.command)) befehle.get(this.command)
          //alert('xxx');
          //this.items.push({message:this.command});
          this.output.push(this.command);
          this.history.push(this.command);
          //this.prompt += this.command;
          //this.$refs.listing.appendChild();
          //this.prompt = befehle[this.command];

          //fx.bind(this);
          //https://alexandernaumov.de/artikel/javascript-apply-call-bind-unterschied
          //fx();

          console.log('main###>',this);
          //befehle[this.command].bind(this)();
          runfn(this,befehle[this.command]);
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

  ul{
    list-style: none;
    alignment: left;
  }
</style>
<template>
    <div id="content">
      {{msg}}
      <img src="../assets/logo.png">
      <gl-shell
          :banner="banner"
          :shell_input="send_to_terminal"
          :commands="commands"
          @shell_output="prompt"
      ></gl-shell>
      <gl-webshell></gl-webshell>
    </div>
</template>

<script>
    import GlShell from "@/components/gl-shell";
    import GlWebshell from "@/components/gl-webshell";

    function func1() {
        //this.msg='ready'
    }

    export default {
        name: "GlContent",
        components: {
          GlShell,
          GlWebshell,
        },
        data() {
          return {
            send_to_terminal: "",
            banner: {
              header: "Vue Shell (CodeSandBox)",
              subHeader: "Shell is power just enjoy 🔥",
              helpHeader: 'Enter "help" for more information.',
              emoji: {
                first: "☠️",
                second: "💀",
                time: 1750
              },
              sign: `VueShell $`,
              img: {
                link: "http://localhost:8080/logo.png",
                //url: "http://localhost:8080/logo.png",
                //src: "http://localhost:8080/logo.png",
                align: "left",
                width: 30,
                height: 30
              }
            },
            commands: [
              {
                name: "info",
                get() {
                  return `<p>With ❤️ By Salah Bentayeb @halasproject.</p>`;
                }
              },
              {
                name: "help",
                get() {
                  return `###############IX###################`
                }
              },
              {
                name: "uname",
                get() {
                  return navigator.appVersion;
                }
              }
            ]
          };
        },
        methods: {
          prompt(value) {
            if (value.trim() === "ifconfig") {
              this.send_to_terminal = `
      Wi-Fi wireless network card:

      Local link IPv6 address. . . : fe80 :: 340f: 6f02: 41e9: 477b% 24
      IPv4 address. . . . . . . . .: 192.168.1.2
      Subnet mask. . . . . . . . . : 255.255.255.0
      Default Gateway. . . . . . . : 192.168.1.1`;
            } else {
              this.send_to_terminal = `'${value}' is not recognized as an internal command or external,
  an executable program or a batch file`;
            }
          },
          ready: func1(),  // {this.Http.get('https://partyx.de').then(response => { this.html = response.data()})}
        },
        props: {
          msg: String
        }
    }
</script>

<style scoped>
  #content {
      border: 1px solid yellow;
      width: 97.5%;
      margin: 1px;
      padding: 1px 1px 1px 1px;
  }
</style>
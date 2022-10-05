<template>
  <div id="app">

    <PowerBIReportEmbed
        :embedConfig = "embedConfig"
        :cssClassName = "cssClassName"
        :phasedEmbedding = "phasedEmbedding"
        :eventHandlers = "eventHandlers"
    >
    </PowerBIReportEmbed>
  </div>
</template>
<script>
import { PowerBIReportEmbed } from 'powerbi-client-vue-js';
import { models} from 'powerbi-client';

export default {
  name: 'DemoApp',

  components: {
    PowerBIReportEmbed,
  },
  data() {
    return {
      embedConfig:{
        type: "report",
        id: "demo",
        embedUrl: "https://app.powerbi.com/view?r=eyJrIjoiMjg2MmQ5ZjktNjk2YS00ZDM1LThhZjEtNWQ4ZjMyMjgyY2VkIiwidCI6IjZiMjIwYTZjLTUwOWMtNDY1Yi1hZWM4LTk5OWNhMjkyMTBiZiIsImMiOjEwfQ%3D%3D",
        accessToken: undefined,
        tokenType: models.TokenType.Embed,
        settings: {
          panes: {
            filters: {
              expanded: false,
              visible: false
            }
          },
          background: models.BackgroundType.Transparent,
        }
      },
      cssClassName: "reportClass",
      phasedEmbedding:  false,
      eventHandlers:new Map(
          [
            ['loaded', () => console.log('Report loaded')],
            ['rendered', () => console.log('Report rendered')],
            ['error', (event) => console.log(event.detail)]
          ]
      ),
    }
  },
  methods: {

  }
}
</script>
<style lang="scss">
#app {
  width: 100%;
  height: 100%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  .reportClass{
    width: 100%;
    height: 100%;
  }
}
html{
  width: 100%;
  height: 100%;
}
body{
  width: 100%;
  height: 100%;
  margin:0px;
}
nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>

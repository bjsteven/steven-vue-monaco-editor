<template>
  <div id="app">
    <!--调用子组件-->
    <monacoEditor ref="monaco" @change="changeValue" :opts="opts" :height="300" :width="800"></monacoEditor>
  </div>
</template>

<script>
import monacoEditor from './components/monacoEditor/'

export default {
  name: 'app',
  components: {
    monacoEditor
  },
  data () {
    return {
        //配置项
         opts: {
          // eslint-disable-next-line
	        value:['function x() {', '\tconsole.log("Hello world!");', '}'].join('\n'),
          autoIndent:true,//启用自动缩进调整。默认为false。
          roundedSelection: true, // 右侧不显示编辑器预览框
          selectOnLineNumbers: true,
          readOnly: false,
          cursorStyle: 'line',
          automaticLayout: false,
          glyphMargin: true,
          theme: 'vs-dark'
        }
    }
  },
      methods: {
      // 手动获取编辑内容
      getValue() {
        this.$message.info(this.$refs.monaco.getVal())
      },
      // 编辑内容
      changeValue(val) {
        // eslint-disable-next-line no-console
        console.log(val)
        this.opts.value = val
      }
    }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  /* color: #2c3e50; */
  margin-top: 60px;
}
</style>

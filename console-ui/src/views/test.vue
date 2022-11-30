<template>
  <div class="main">
    <div class="/test" v-html="htmlPage">
    </div>
    <div id="tabBox" class="tabBox"></div>

    <div id="container"></div>

  </div>
</template>

<script>
import request from '@/utils/request'
import ButtonCounter from '../components/ButtonCounter';
import Vue from 'vue';


export default {
  name: "test",
  components: {
    ButtonCounter,
  },
  data(){
    return {
      loginForm: {
        username: "aaa"
      },
      htmlPage: "",
      tabName: '',
      base: '页签',
      num: 1
    }
  },
  mounted() {
    this.insert();
  },
  methods:{
    readFile(filePath) {
      // 创建一个新的xhr对象
      let xhr = null
      if (window.XMLHttpRequest) {
        xhr = new XMLHttpRequest()
      } else {
        // eslint-disable-next-line
        xhr = new ActiveXObject('Microsoft.XMLHTTP')
      }
      const okStatus = document.location.protocol === 'file' ? 0 : 200
      xhr.open('GET', filePath, false)
      xhr.overrideMimeType('text/html;charset=utf-8')
      xhr.send(null)
      return xhr.status === okStatus ? xhr.responseText : null
    },
    test(){
      // request({
      //   url: '/',
      //   method: 'get',
      // }).then(res=>{
      //   console.log(res)
      //   this.htmlPage = res;
      //   console.log(this.htmlPage)
      // })
      this.htmlPage = "      <el-popover\n" +
        "        placement=\"top-start\"\n" +
        "        title=\"标题\"\n" +
        "        width=\"200\"\n" +
        "        trigger=\"hover\"\n" +
        "        content=\"这是一段内容,这是一段内容,这是一段内容,这是一段内容。\">\n" +
        "        <el-button slot=\"reference\">hover 激活</el-button>\n" +
        "      </el-popover>";
      this.$forceUpdate()

    },
    insert() {

      // Vue.component('button-counter', {
      //   data: function () {
      //     return {
      //       count: 0
      //     }
      //   },
      //   template: '<button v-on:click="count++">You clicked me {{ count }} times.</button>'
      // })

      let a = {
        "name": "ButtonCounter",
        "staticRenderFns": [],
        "_compiled": true,
        "beforeCreate": [
          null
        ],
        "beforeDestroy": [
          null
        ],
        "__file": "src/components/ButtonCounter.vue",
        "_Ctor": {}
      }


      // request({
      //   url: '/download',
      //   method: 'post',
      // }).then(res=>{
      //   let info = require(res).default;
      //   console.log(res)
      //   // this.htmlPage = res;
      //   // console.log(this.htmlPage)
      //   console.log(info)
      //   // console.log(ButtonCounter)
      //   const bcConstructor = Vue.extend(info);
      //   const instance = new bcConstructor();
      //   instance.$mount('#container');
      // })

      let info = require(`D://a.vue`).default;
      console.log(info)
      // console.log(ButtonCounter)
      const bcConstructor = Vue.extend(info);

      const instance = new bcConstructor();
      instance.$mount('#container');
    },
    text1(){
      render:(h)=>{
        h(
          'div',
          [
            h('p', 'Hello'),
            ' world!'
          ]
        )
      }
    }
  },

}
</script>

<style scoped>

</style>

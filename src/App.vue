<template>
  <div id="app">
    <div class="container-fluid">
      <Header></Header>
      <div class="row main">
      <Siderbar v-bind:info="info"></Siderbar>
      <Content v-bind:contents="{
          works:works,
          education:education,
          projects:projects,
          productions:productions,
          skills:skills,
          languages:languages
      }"></Content>
      <Footer v-bind:info="info"></Footer>
      </div>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
import Header from '@/components/Header';
import Footer from '@/components/Footer';
import Siderbar from '@/components/Siderbar';
import Content from '@/components/Content';

export default {
  name: 'App',
  components: {
		Header,
    Footer,
    Siderbar,
    Content
  },
  data(){
        return{
            info: {},
            works:[],
            education:{},
            projects:[],
            productions:[],
            skills:[],
            languages:{}
        }
  },
    mounted() {
        // 调用getJson方法
        this.getJson()
    },
    methods: {
        getJson(){
            // 获取本地json
            const url = '../static/resume.json'
            this.$http.get(url).then((res)=>{
                this.info = res.data.info;
                this.works = res.data.works;
                this.education = res.data.education;
                this.projects = res.data.projects;
                this.skills =res.data.skills;
                this.languages = res.data.languages;
                this.productions = res.data.productions;
                // console.log(typeof(this.work))
            })
        }
    }
}
</script>

<style>
*{
  margin:0;
  padding:0;
}
#app {
  font-family: Helvetica Neue For Number,
               -apple-system,BlinkMacSystemFont,Segoe UI,Roboto,PingFang SC,Hiragino Sans GB,Microsoft YaHei,
               Helvetica Neue,Helvetica,Arial,sans-serif;
               -webkit-font-smoothing: antialiased;
               -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body{
  background-color: #f0f0f0;
}
.row{
  padding:5px;
}
@media (max-width: 992px) {
  .siderbar{
    position: relative;
  }
}
</style>

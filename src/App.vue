<template>
<navbar
  v-if="pages.length > 0"
  :pages="pages"
  :text="pages[activePage]"
  :theme="theme"
  :change="changeTheme"
  :modo="getTema()"
  :func="(index) => activePage = index">
</navbar>
<page-viewer 
    v-if="pages.length > 0"
    :title="pages[activePage].pageTitle"
    :modo = "getTema()">
</page-viewer>
<create-page
    :pageCreated="createPage">
</create-page>

</template>

<script>
import PageViewer from './components/PageViewer.vue'
import Navbar from './components/Navbar.vue'
import CreatePage from './components/CreatePage.vue'


export default{
  components:{
    Navbar, PageViewer, CreatePage
  },
  created(){
    this.getPages();
  },
  data(){
      return{
        theme:'light',
        activePage: 0,
        pages: []
      }
    },
  methods:
  {
    changeTheme() 
    {
      this.theme = this.theme === 'light' ? 'dark' : 'light';
    },
    getTema() 
    {
      return this.theme === 'light' ? 'Modo Branco' : 'Modo Escuro';
    },
    async getPages(){
      let res = await fetch('pages.json');
      let data = await res.json()
      this.pages = data;
    },
    createPage(pageObj){
      console.log(pageObj)
      this.pages.push(pageObj)
    }
  }
}

</script>


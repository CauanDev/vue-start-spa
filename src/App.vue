<template>
    <navbar
      :pages = "pages"
      :text = "pages[activePage]"
      :theme = "theme"
      :change="changeTheme"
      :modo= "getTema()"
      :func ="(index)=>activePage = index">
    </navbar>
    <pageviewer 
      :title="pages[activePage].link.text"
      :modo = "getTema()">
    </pageviewer>
</template>

<script>
import PageViewer from './components/PageViewer.vue'
import Navbar from './components/Navbar.vue'


export default{
  components:{
    Navbar, PageViewer
  },
  data(){
      return{
        theme:'light',
        activePage: 0,
        pages: [
                  {
                      link: {url: 'index.html' , text:'Home'},
                      pageTitle:'Hello vue, you are in the Index',
                      pageContent:'Welcome to my training with vue'
                  },
                  {
                      link: {url: 'about.html' , text:'About'},
                      pageTitle:'Hello vue, you are in the About',
                      pageContent:'Welcome to my training with vue'
                  },
                  {
                      link: {url: 'contact.html' , text:'Contact'},
                      pageTitle:'Hello vue, you are in the Contact',
                      pageContent:'Welcome to my training with vue'
                  }
              ]
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
    }
  }
}

</script>


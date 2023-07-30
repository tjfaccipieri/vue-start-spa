<template>
  <Navbar :pages="pages" :active-page="activePage" :nav-link-click="(index) => activePage = index"></Navbar>
  <PageViewer :page="pages[activePage]"></PageViewer>
</template>

<script>
  import Navbar from './components/Navbar.vue'
  import PageViewer from './components/PageViewer.vue'

  const links = [
    {
            link: {text: 'Home', url: 'index.html'},
            pageTitle: "Home page",
            content: "This is the home page"
          },
          {
            link: {text: 'About', url: 'about.html'},
            pageTitle: "About page",
            content: "This is the about page"
          },
          {
            link: {text: 'Contact', url: 'contact.html'},
            pageTitle: "Contact page",
            content: "This is the contact page"
          },
  ]

  export default {
    components: {
      Navbar,
      PageViewer,
    },

    data() {
      return {
        activePage: 0,
        pages: links,
      }
    }
  }
</script>
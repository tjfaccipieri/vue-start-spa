<template>
  <Navbar
    :pages="pages"
    :active-page="activePage"
    :nav-link-click="(index) => (activePage = index)"
  ></Navbar>



  <!-- <PageViewer :page="pages[activePage]"></PageViewer> -->

  <create-page
    :page-created="pageCreated"
  ></create-page>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import PageViewer from "./components/PageViewer.vue";
import CreatePage from "./components/CreatePage.vue";

export default {
  components: {
    Navbar,
    PageViewer,
    CreatePage
  },
  created() {
    this.getPages();
  },

  data() {
    return {
      activePage: 0,
      pages: [],
    };
  },
  methods: {
    async getPages() {
      let res = await fetch("pages.json");
      let data = await res.json();

      this.pages = data;
    },

    async getList() {
      let res = await fetch("https://jsonplaceholder.typicode.com/users");
      let data = await res.json();

      this.pages = data;
    },

    pageCreated(pageObj) {
      console.log(pageObj);
    }
  },
};
</script>

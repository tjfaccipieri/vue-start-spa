<template>
  <nav
    :class="[`navbar-${theme}`, `bg-${theme}`, 'navbar', 'navbar-expand-md']"
  >
    <div class="container-fluid">
      <a class="navbar-brand" href="#">My View SPA</a>
      <ul class="navbar-nav me-auto mb-lg-0 mb-2">
        <li v-for="(page, index) in pages" :key="index" class="nav-item">
          <navbar-link
            :page="page"
            :isActive="activePage === index"
            @click.prevent="navLinkClick(index)"
          >
          </navbar-link>
        </li>
      </ul>
      <form class="d-flex">
        <button class="btn btn-primary" @click.prevent="changeTheme()">
          Toogle Theme
        </button>
      </form>
    </div>
  </nav>
</template>

<script>
import NavbarLink from './NavbarLink.vue';
export default {
  components: {
    NavbarLink,
  },

  created(){
    this.getThemeSetting()
  },
  
  props: ['pages', 'activePage', 'navLinkClick'],

  data() {
    return {
      theme: 'light',
    };
  },
  methods: {
    changeTheme() {
      let theme = 'light';

      if (this.theme === 'light') {
        theme = 'dark';
      }

      this.theme = theme;
      this.storeThemeSetting()
    },
    storeThemeSetting() {
      localStorage.setItem('theme', this.theme);
    },
    getThemeSetting() {
      let theme = localStorage.getItem('theme');

      if (theme) {
        this.theme = theme;
      }
    },
  },
};
</script>

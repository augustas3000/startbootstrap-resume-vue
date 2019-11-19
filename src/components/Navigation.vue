<template>
  <b-navbar toggleable="lg" type="dark" class="bg-primary fixed-top" id="sideNav">
    <b-navbar-brand to="#app">
      <span class="d-block d-lg-none">{{ name.first }} {{ name.last }}</span>
      <span class="d-none d-lg-block">
        <b-img-lazy
          class="img-profile rounded-circle mx-auto mb-2"
          src="images/profile.jpg"
<<<<<<< HEAD
          :alt="name"
        ></b-img-lazy>
=======
          :alt="name.first + ' ' + name.last"
        />
>>>>>>> master
      </span>
    </b-navbar-brand>
    <b-navbar-toggle target="navbarSupportedContent"></b-navbar-toggle>
    <b-collapse id="navbarSupportedContent" is-nav>
      <b-navbar-nav v-b-scrollspy>
        <b-nav-item
          v-for="(navigation, index) in navigationList"
          :key="index"
          class="js-scroll-trigger"
          :href="navigation.url"
        >{{ navigation.title }}</b-nav-item>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>

<script>
export default {
  name: "Navigation",
  props: {
    name: Array
  },
  data() {
    return {
      name: "Clarence Taylor",
      navigationList: []
    };
  },
  mounted: async function() {
    try {
      const res = await this.$axios.get("/navigation");
      this.navigationList = res.data;
    } catch (e) {
      console.log(e);
    }
  }
};
</script>
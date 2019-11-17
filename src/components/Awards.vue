<template>
  <section id="awards" class="resume-section p-3 p-lg-5 d-flex align-items-center">
    <div class="w-100">
      <h2 class="mb-5">Awards &amp; Certifications</h2>
      <ul class="fa-ul mb-0">
        <li v-for="(award, index) in awardsList" :key="index" class="d-flex align-items-center">
          <font-awesome-icon :icon="['fas', 'trophy']" class="fa-li text-warning"></font-awesome-icon>
          {{ award }}
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  name: "Awards",
  data() {
    return {
      awardsList: []
    };
  },
  mounted: async function() {
    try {
      const res = await this.$axios.get('/awards')
      this.awardsList = res.data
    } catch (e) {
      console.log(e)
    }
  }
};
</script>
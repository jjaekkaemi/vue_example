<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h2>move data {{ this.$route.params.parmas_data }}</h2>
  </div>
</template>
<script>
export default {
  props: {
    parmas_data: {
      type: String,
    },
  },
};
</script>

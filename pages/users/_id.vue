<template>
  <div>
    <p>
      /user/_id.vue
    </p>
    <p>
      User ID:{{userId}}
    </p>
  </div>
</template>

<script>
  export default {
    name: "id.vue",
    data() {
      return {
        userId: this.$route.params.id
      }
    }
  }
</script>

<style scoped>

</style>

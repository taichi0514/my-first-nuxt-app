<template>

</template>

<script>
  export default {
    name: "axios",
    $axios.onRequest((config) => {
      if (process.env.QIITA_TOKEN) {
        config.headers.common['Authorization'] = process.env.QIITA_TOKEN
      }
      return config
    })
  }
</script>

<style scoped>

</style>

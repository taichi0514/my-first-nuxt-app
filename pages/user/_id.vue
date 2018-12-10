<template>
  <section class="container">
    <div>
      <h3>{{user.id}}</h3>
      <img src="user.profile_images_url" width="120" alt="">
    </div>
  </section>
</template>

<script>
  export default {
    async asyncData({route,app}){
      const user = await app.$axios.$get(`https://qiita.com/api/v2/users/${route.params.id}`)
      const items = await app.$axios.$get(`https://qiita.com/api/v2/items?query=user:${route.params.id}`)
      return {user,items}
    }
  }
</script>

<style scoped>

</style>

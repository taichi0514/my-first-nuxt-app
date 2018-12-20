<template>
  <section class="container">
    <div>
      <h3>{{user.id}}</h3>
      <div class="user_description">
        <img :src="user.profile_image_url" width="120" alt="">
        <p class="description">{{user.description || 'No description'}}</p>
      </div>
      <p class="btn_returm">
        <nuxt-link to="/">トップに戻る</nuxt-link>
      </p>
      <h3>{{user.id}}さんの投稿一覧</h3>
      <ul>
        <li v-for="item in items" :key="item.id">
          <h4><a :href="item.url">{{item.title}}</a></h4>
          <div>{{item.body.slice(0,130)}}......</div>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
  import {mapGetters} from 'vuex'
  export default {
    head() {
      return {
        title: this.user.id
      }
    },
    async asyncData({route, store, redirect}) {
      if (store.getters['users'][route.params.id]) {
        return
      }
      try {
        await store.dispatch('fetchUserInfo', {id: route.params.id})
      } catch (e) {
        redirect('/')
      }
    },
    computed: {
      user() {
        return this.users[this.$route.params.id]
      }
    }
  }
</script>

<style scoped>
  h3 {
    font-size: 2rem;
    border-bottom: #47494e 3px solid;
    padding: 0 15px;
  }

  .user_description {
    display: flex;
    padding: 15px 15px 0;
  }

  .user_description img {
    /*margin-top: 20px;*/
    /*margin-top: 20px;*/
  }

  .user_description .description {
    margin-left: 20px;
  }

  .btn_returm {
    text-align: right;
    padding: 0 15px;
  }

  li {
    margin-top: 20px;
    text-align: left;
  }

</style>

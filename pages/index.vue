<template>
  <section class="container">
    <div class="login">
      <h2>login関連</h2>
      <ul>
        <li>
          <nuxt-link to="/login">ログインページ</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/authed-route">認証が必要なページへ</nuxt-link>
        </li>
      </ul>
    </div>
    <div>
      <h2>mannzi</h2>
      <h3>nuxt.jsのタグが付けられた投稿一覧</h3>
      <ul>
        <li v-for="item in items" :key="item.id">
          <h4><span>{{item.title}}</span>
            <small><span>by</span>
              <nuxt-link :to="`/user/${item.user.id}`">
                {{item.user.id}}
              </nuxt-link>
            </small>
          </h4>
          <div>{{item.body.slice(0,130)}}......</div>
          <p><a :href="item.url">{{item.url}}</a></p>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
  import {mapGetters} from 'vuex'
  export default {
    async asyncData({store}) {
      if (store.getters['items'].length) {
        return
      }
      await store.dispatch('fetchItems')
    },
    computed: {
      ...mapGetters(['items'])
    }
  }
</script>

<style>
  .container {
    min-height: 100vh;
    display: flex;
    justify-content: start;
    align-items: center;
    text-align: center;
    flex-direction: column;
  }

  .title {
    font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
    display: block;
    font-weight: 300;
    font-size: 100px;
    color: #35495e;
    letter-spacing: 1px;
  }

  .subtitle {
    font-weight: 300;
    font-size: 42px;
    color: #526488;
    word-spacing: 5px;
    padding-bottom: 15px;
  }

  .links {
    padding-top: 15px;
  }


</style>


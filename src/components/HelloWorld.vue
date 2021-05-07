<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>Vue JS Assignment by Palak Bansal</h1>
    <ul>
      <li v-for="(article, index) in articles" :key="index">
        {{ article.author }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data () {
    return {
      articles: {}
    }
  },
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted () {
    this.getAuthor()
  },
  methods: {
    getAuthor() {
      return this.axios({
        url: `https://jsonmock.hackerrank.com/api/articles`,
        method: 'GET'
      }).then((res) => {
        this.articles = (Object.values(res)[0].data)
        console.log(this.articles)
      }).catch((e) => {
          console.log(e)
        })
    }
  }
}
</script>

<template>
  <section class="container">
    <div>
      <MainHeader/>
      <ul>
        <li v-for="article of articles" :v-if="article" :key="article.id">
          <ArticleCard :data="article"/>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
import MainHeader from '~/components/main-header.vue'
import axios from 'axios'
import ArticleCard from '~/components/item-article-card.vue'

export default {
  async asyncData() {
    const { data } = await axios.get(`http://admin.fausfore.eu/article`)
    return { articles: data }
  },
  components: {
    ArticleCard,
    MainHeader
  }
}
</script>


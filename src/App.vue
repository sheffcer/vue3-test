<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Актуальные новости  {{now}}</h2>
      <span>Открыто раз: {{openRate}}</span>
    </div>
      <app-news
      v-for="item in news"
      :key="item.id"
      :title="item.title"
      :id="item.id"
      :is-open="item.isOpen"
      @open-news="openNews"
      ></app-news>
  </div>
</template>
<script>
import AppNews from './AppNews.vue'
export default {
  data () {
    return {
      now: new Date().toLocaleDateString(),
      openRate: 0,
      // isOpen: false,
      news: [
        {
          id: 1,
          title: 'Красюк: Усик не давал согласия на бой Джошуа и Фьюри',
          isOpen: false
        },
        {
          id: 2,
          title: 'Под Запорожьем митингуют против строительства карьера по добыче каолина',
          isOpen: false
        },
        {
          id: 3,
          title: 'Брайан Остин Грин подтвердил новые отношения',
          isOpen: false
        }
      ]
    }
  },
  components: {
    AppNews
  },
  methods: {
    openNews () {
      this.openRate++
    }
  }
}
</script>

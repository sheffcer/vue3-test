<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Актуальные новости  {{now}}</h2>
      <span>Открыто раз: {{openRate}}</span>
      <span> Прочитано раз: {{marked}}</span>
    </div>
      <app-news
      v-for="item in news"
      :key="item.id"
      :title="item.title"
      :text="item.text"
      :id="item.id"
      :is-open="item.isOpen"
      :was-read="item.wasRead"
      @open-news="openNews"
      @mark-read="markedNews"
      @unmark-read="unmarkedNews"
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
      marked: 0,
      // isOpen: false,
      news: [
        {
          id: 1,
          title: 'Киев попал в сотню самых зеленых городов мира',
          text: 'Часть городских зеленых насаждений в украинской столице составляет 44%, что дало возможность городу занять сотое место в списке самых зеленых городов мира',
          isOpen: false,
          wasRead: false
        },
        {
          id: 2,
          title: 'Роналду - лучший бомбардир национальных чемпионатов в XXI веке',
          text: 'Португалец забил 462 гола в XXI веке. Звездный форвард Ювентуса Криштиану Роналду был назван лучшим бомбардиром мировых лиг в XXI веке по версии Международной федерации футбольной истории и статистики (IFFHS)',
          isOpen: false,
          wasRead: false
        },
        {
          id: 3,
          title: 'Капитолий огородят во время инаугурации Байдена',
          text: 'На территорию Капитолия смогут попасть только приглашенные лица, которые имеют билеты. Вход для остальной публики будет закрыт',
          isOpen: false,
          wasRead: false
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
    },
    markedNews (id) {
      this.marked++
      // console.log(id)
      const idx = this.news.findIndex(news => news.id === id)
      this.news[idx].wasRead = true
      console.log(idx)
    },
    unmarkedNews (id) {
      this.marked--
      const idx = this.news.findIndex(news => news.id === id)
      this.news[idx].wasRead = false
      console.log(idx)
    }
  }
}
</script>

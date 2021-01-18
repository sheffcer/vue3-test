<template>
<div class="card">
  <h3>{{title}}</h3>
  <app-button
  @action="open"
  :class="{ 'btn--close' : isOpenLocal }"
  >
  {{isOpenLocal ? 'Закрыть' : 'Открыть'}}
  </app-button>
  <div v-if="isOpenLocal">
  <p>{{text}}</p>
  <app-button
  v-if="wasRead"
  color="danger"
  @action="unmark"
  >Отметить как непрочитанным
  </app-button>
  <app-button
  v-if="!wasRead"
  color="primary"
  @action="read"
  >
  {{!isLocalMarked ? 'Пометить как прочитанное' : 'Прочитано'}}
  </app-button>
  <app-news-list ></app-news-list>
  </div>
</div>
</template>

<script>
import AppButton from './AppButton.vue'
import AppNewsList from './AppNewsList.vue'
export default {
  emits: {
    'open-news': null,
    'mark-read' (id) {
      if (id) {
        return true
      }
      console.log('нет валидируемого параметра для данного $emit ')
      return false
    },
    'unmark-read' (id) {
      if (id) {
        return true
      }
      console.log('нет валидируемого параметра для данного $emit ')
      return false
    }
  },
  props: {
    wasRead: Boolean,
    title: {
      type: String,
      required: true
    },
    text: {
      type: String,
      required: true
    },
    id: {
      type: Number,
      required: true
    },
    isOpen: {
      type: Boolean,
      required: false,
      default: false,
      validator (value) {
        // console.log(value)
        return true
      }
    }
  },
  data () {
    return {
      item: 'item string',
      isOpenLocal: this.isOpen,
      isLocalMarked: false
    }
  },
  methods: {
    open () {
      this.isOpenLocal = !this.isOpenLocal
      if (this.isOpenLocal) {
        this.$emit('open-news') // название события отправляемого наверх
      }
    },
    read () {
      this.isOpenLocal = !this.isOpenLocal
      // if (this.wasRead) {
      this.$emit('mark-read', this.id)
      // }
    },
    unmark () {
      this.$emit('unmark-read', this.id)
    }
  },
  components: {
    AppButton,
    AppNewsList
  }
}
</script>

<style lang="css" scoped>
  .btn--close {
    /* color: red;
    border: 1px solid red;
    transition: all 0.22s; */
  }
</style>

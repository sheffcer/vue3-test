<template>
<div class="card">
  <h3>{{title}}</h3>
  <button
  class="btn"
  @click="open"
  :class="{ 'btn--close' : isOpenLocal }"
  >
    {{isOpenLocal ? 'Закрыть' : 'Открыть'}}
  </button>
  <button
  class="btn"
  v-if="isOpenLocal"
  :class="{ 'btn--close' : isLocalMarked }"
  @click="read"
  >{{!isLocalMarked ? 'Пометить как прочитанное' : 'Прочитано'}}
  </button>
  <p v-if="isOpenLocal">{{text}}</p>
</div>
</template>

<script>
export default {
  props: {
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
        console.log(value)
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
      this.isLocalMarked = !this.isLocalMarked
      if (this.isLocalMarked) {
        this.$emit('mark-read')
      }
    }
  }
}
</script>

<style lang="css" scoped>
  .btn--close {
    color: red;
    border: 1px solid red;
    transition: all 0.22s;
  }
</style>

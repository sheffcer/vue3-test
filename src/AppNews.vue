<template>
<div class="card">
  <h3>{{title}}</h3>
  <button class="btn" @click="open">
    {{isOpenLocal ? 'Закрыть' : 'Открыть'}}
  </button>
  <p v-if="isOpenLocal">Lorem ipsum dolor sit amet consectetur adipisicing elit. Praesentium, optio!</p>
</div>
</template>

<script>
export default {
  props: {
    title: {
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
      isOpenLocal: this.isOpen
    }
  },
  methods: {
    open () {
      this.isOpenLocal = !this.isOpenLocal
      if (this.isOpenLocal) {
        this.$emit('open-news') // название события отправляемого наверх
      }
    }
  }
}
</script>

<style lang="scss" scoped>

</style>

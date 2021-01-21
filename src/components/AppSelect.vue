<template>
  <div class="form-control">
    <label for="city">Твой город</label>
    <select id="city" :selected="selected">
      <option
      v-for="option in options"
      :key="option"
      :value=option.value
      @change="onSelect"
      >{{option.tag}}</option>
    </select>
    </div>
</template>

<script>
export default {
  emits: ['update:value'],
  props: {
    options: {
      type: Array,
      required: true
    },
    selected: String,
    tabindex: {
      type: Number,
      required: false,
      default: 0
    }
  },
  methods: {
    onSelect (evt) {
      this.$emit('update:value', evt.option.value)
    }
  }
}
</script>

<style lang="scss">

</style>

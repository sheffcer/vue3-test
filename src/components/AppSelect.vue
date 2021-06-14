<template>
  <div class="form-control">
    <label for="city">Твой город</label>
    <select id="city" @change="onChange($event)">
      <option
      v-for="option in options"
      :key="option"
      :value="option.value"
       @click="$emit('input', option.value)"
      >{{option.tag}}</option>
    </select>
    </div>
</template>

<script>
export default {
  emits: ['update:selected', 'change:selected', 'input'],
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
      this.$emit('update:selected', evt.target.value)
      console.log(event.target.value)
      // @changeSelect="$emit('change', $event.target.value)"
    },
    selectOption (option) {
      this.$emit('input', option)
    },
    onChange (event) {
      this.$emit('change:selected', event.target.value)
      console.log(event.target.value)
    }
  }
}
</script>

<style lang="scss">

</style>

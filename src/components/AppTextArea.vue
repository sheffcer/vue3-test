<template>
  <div class="form-control">
    <p>{{title}}</p>
      <textarea
      id="text-aria"
      rows="3"
      :placeholder="placeholder"
      :value="modelValue"
      @input="onChange"
      ></textarea>
  </div>
</template>

<script>
export default {
  emits: ['update:modelValue'],
  props: {
    placeholder: String,
    title: String,
    modelValue: String
  },
  methods: {
    onChange (evt) {
      this.$emit('update:modelValue', evt.target.value)
    }
  }
}
</script>

<style lang="scss" scoped>

</style>

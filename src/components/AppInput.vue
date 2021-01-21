<template>
      <div class="form-control" :class="{invalid: error}">
        <label :for="id">{{label}}</label>
        <input
        type="text"
        :id="id"
        :placeholder="placeholder"
        :value="modelValue"
        @change="onChange"
        :error="error"
        >
        <small v-if="error">{{error}}</small>
      </div>
</template>
<script>
export default {
  emits: ['update:modelValue'],
  props: {
    modelValue: String,
    placeholder: String,
    label: {
      type: String
    },
    error: {
      type: String
    }
  },
  data () {
    return {
      id: 'input' + Math.random()
    }
  },
  methods: {
    onChange (evt) {
      this.$emit('update:modelValue', evt.target.value)
    }
  }
}
</script>

<style lang="scss">

</style>

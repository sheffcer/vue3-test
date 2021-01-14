<template>
  <div>
    <button class=btn></button>
  </div>
</template>

<script>
  export default {
    props: {
    text: String,
    color: {
      type: String,
      default: '',
      validator (value) {
        return ['', 'primary', 'danger'].includes(value)
      }
    }
    }
  }
</script>

<style lang="scss" scoped>

</style>

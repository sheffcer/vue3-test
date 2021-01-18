<template>
  <div class=card>
    <slot name="header"></slot>
    <slot name="default">
      no text
    </slot>
    <div f-if="$slots.footer">
    <slot name="footer"></slot>
    </div>
  </div>
</template>

<script>
export default {
  mounted () {
    console.log(this.$slots)
  }
}
</script>

<style lang="scss" scoped>

</style>

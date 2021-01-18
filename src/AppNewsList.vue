<template>
  <div>
    <hr/>
    <h4>{{title}}</h4>
    <u>
      <li v-for="item in news" :key="item">{{item.title}}</li>
    </u>
  </div>
</template>

<script>
export default {
  inject: ['title', 'news']
}
</script>

<style lang="scss" scoped>

</style>

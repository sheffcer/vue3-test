<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Слоты</h2>
      <app-list>
        <template #default="slotProps">
          <span style="color: orange">
            <strong>{{slotProps.idx}}</strong>
            {{slotProps.iter}}</span>
        </template>
      </app-list>
      <app-block>
        <p>Mazafaka!!!</p>
        <template v-slot:header>
        <h3>Заголовок</h3>
        </template>
        <template #footer>
          <hr/>
          <small>Футер</small>
        </template>
      </app-block>
    </div>
  </div>
</template>
<script>
import AppBlock from './AppBlock'
import AppList from './AppList'
export default {
  components: {
    AppBlock,
    AppList
  }
}
</script>

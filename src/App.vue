<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Табы</h2>
      <div class="tabs">
        <app-button
        :color="active === 'one' ? 'primary' : ''"
        @action="active = 'one'"
          >one tab
        </app-button>
        <app-button
        :color="active === 'two' ? 'primary' : ''"
        @action="active = 'two'"
        >two tab </app-button>
        <app-button
        :color="active === 'three' ? 'primary' : ''"
        @action="active = 'three'">
        three tab </app-button>
      </div>
    </div>
  </div>
</template>
<script>
import AppButton from './AppButton'
export default {
  data () {
    return {
      active: 'one'
    }
  },
  components: {
    AppButton
  }
}
</script>

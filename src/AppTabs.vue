<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Табы</h2>
      <div class="tabs">
        <app-button
        ref="myBtn"
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
        <!-- <app-text-one
        v-if="active === 'one'"
        style="display:block"
        ></app-text-one>
        <app-text-two
        v-else-if="active === 'two'"
        style="display:block"
        ></app-text-two>
        <app-text-three
        v-else-if="active === 'three'"
        style="display:block"></app-text-three> -->
        <keep-alive>
        <component :is="componentNameMod"></component>
        </keep-alive>
      </div>
  </div>
</template>
<script>
import AppButton from './AppButton'
import AppTextOne from './components/AppTextOne'
import AppTextTwo from './components/AppTextTwo'
import AppTextThree from './components/AppTextThree'
export default {
  data () {
    return {
      active: 'one'
    }
  },
  components: {
    AppButton,
    AppTextOne,
    AppTextTwo,
    AppTextThree
  },
  mounted () {
    console.log(this.$refs.myBtn)
  },
  computed: {
    componentName () {
      if (this.active === 'one') {
        return 'app-text-one'
      } else if (this.active === 'two') {
        return 'app-text-two'
      } else return 'app-text-three'
    },
    componentNameMod () {
      console.log(`app-text-${this.active}`)
      return `app-text-${this.active}`
    },
    colorName () {
      return this.active === 'one' ? 'primary' : ''
    }
  }
}
</script>

<template>
  <div class="container">
    <form class="card" @submit.prevent="submitHeandler">
      <h1>Анкета на Vue разработчика!</h1>
      <div class="form-control">
        <label for="name">Как тебя зовут?</label>
        <input
        v-model.trim="name"
        type="text"
        id="name"
        placeholder="Введи имя">
      </div>

      <div class="form-control">
        <label for="age">Выбери возраст</label>
        <input
        v-model.number="age"
        ref="inputName"
        type="number"
        id="age"
        >
      </div>

      <div class="form-control">
        <label for="city">Твой город</label>
        <select id="city" v-model="city">
          <option value="spb">Санкт-Петербург</option>
          <option value="msk">Москва</option>
          <option value="kzn">Казань</option>
          <option value="nsk">Новосибирск</option>
        </select>
      </div>

      <div class="form-checkbox">
        <span class="label">Готов к переезду в Токио?</span>
        <div class="checkbox">
          <label><input type="radio" name="trip" v-model="relocate" value="yes"/> Да</label>
        </div>

        <div class="checkbox">
          <label><input type="radio" name="trip" v-model="relocate" value="no"/> Нет</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label">Что знаешь во Vue?</span>
        <div class="checkbox">
          <label><input
          type="checkbox"
          name="skills"
          v-model="skills"
          value="vuex"/> Vuex</label>
        </div>
        <div class="checkbox">
          <label><input
          type="checkbox"
          name="skills"
          v-model="skills"
          value="cli"/> Vue CLI</label>
        </div>
        <div class="checkbox">
          <label><input
          type="checkbox"
          name="skills"
          v-model="skills"
          value="router"/> Vue Router</label>
        </div>
      </div>
      <div class="form-checkbox">
        <span class="label">Соглашаюсь с уловиями</span>
        <div class="checkbox">
          <label><input type="checkbox" v-model="agree"/>Да</label>
        </div>
      </div>

      <!-- <button type="submit" class="btn primary">Отправить</button> -->
      <app-button color="primary" type="submit">{{submit}}</app-button>
    </form>
  </div>
</template>

<script>
import AppButton from './AppButton.vue'
export default {
  data () {
    return {
      name: '',
      age: 33,
      city: 'msk',
      relocate: null,
      skills: [],
      agree: false,
      submit: 'Отправить'
    }
  },
  components: {
    AppButton
  },
  methods: {
    submitHeandler () {
      // evt.preventDefault()
      console.group('Form Data')
      console.log('Имя: ', this.name)
      console.log('Имя ref: ', this.$refs.inputName.value)
      console.log('Возраст: ', this.age)
      console.log('Город: ', this.city)
      console.log('Релокейт: ', this.relocate)
      console.log('Скилы: ', this.skills)
      console.log('Согласен: ', this.agree)
      console.groupEnd()
    }
  }
}
</script>

<style>

</style>

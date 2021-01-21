<template>
  <div class="container">
    <form class="card" @submit.prevent="submitHeandler">
      <h1>Test!</h1>
      <app-input
      placeholder="Введи имя"
      label="Как тебя зовут?"
      v-model="name"
      ></app-input>
      <!-- <div class="form-control" :class="{invalid: errors.name}">
        <label for="name">Как тебя зовут?</label>
        <input
        v-model.trim="name"
        type="text"
        id="name"
        placeholder="Введи имя">
        <small v-if="errors.name">{{errors.name}}</small>
      </div> -->

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
import AppInput from './components/AppInput.vue'
export default {
  data () {
    return {
      name: '',
      age: 33,
      city: 'msk',
      relocate: null,
      skills: [],
      agree: false,
      submit: 'Отправить',
      errors: {
        name: null
      }
    }
  },
  components: {
    AppButton,
    AppInput
  },
  methods: {
    submitHeandler () {
      // evt.preventDefault()
      if (this.formIsValid()) {
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
    },
    formIsValid () {
      let isValid = true
      if (this.name.length === 0) {
        this.errors.name = 'Введите имя'
        isValid = false
      } else {
        this.errors.name = null
      }
      return isValid
    }
  }
}
</script>

<style>
  .form-control small {
    color:#e53935;
  }

  .form-control.invalid input {
    border-color:#e53935;
  }
</style>

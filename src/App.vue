<template>
  <div class="container">
    <form class="card" @submit.prevent="submitHeandler">
      <h1>Test!</h1>
      <app-input
      placeholder="Введи имя"
      label="Как тебя зовут?"
      v-model.trim="name"
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
      <app-select
      v-model="selected"
      :options="options"
      :selected="selected"
      @change:selected="selected = $event"
      >{{selected}}</app-select>
      <!-- <div class="form-control">
        <label for="city">Твой город</label>
        <select id="city" v-model="selected">
          <option value="spb">Санкт-Петербург</option>
          <option value="msk">Москва</option>
          <option value="kzn">Казань</option>
          <option value="nsk">Новосибирск</option>
        </select>
      </div> -->

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
      <!-- <div class="form-control">
        <p>Черканите пару строк</p>
      <textarea
      id="text-aria"
      rows="3"
      v-model="message"
      placeholder="введите сюда свою чухню"
      ></textarea>
      </div> -->
      <app-text-area
      v-model.trim="message"
      title="Новая чухня"
      placeholder="введите сюда вашу чухню"
      ></app-text-area>
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
import AppSelect from './components/AppSelect.vue'
// import AppTextAria from '@/components/AppTextAria'
import AppTextArea from './components/AppTextArea.vue'
export default {
  data () {
    return {
      name: '',
      age: 33,
      selected: 'od',
      relocate: null,
      skills: [],
      agree: false,
      message: '',
      submit: 'Отправить',
      errors: {
        name: null
      },
      options: [
        {
          value: 'od',
          tag: 'Одесса'
        },
        {
          value: 'kv',
          tag: 'Киев'
        },
        {
          value: 'kh',
          tag: 'Харьков'
        }
      ]
    }
  },
  components: {
    AppButton,
    AppInput,
    AppSelect,
    AppTextArea
  },
  methods: {
    submitHeandler () {
      // evt.preventDefault()
      if (this.formIsValid()) {
        console.group('Form Data')
        console.log('Имя: ', this.name)
        // console.log('Имя ref: ', this.$refs.inputName.value)
        console.log('Возраст: ', this.age)
        console.log('Город: ', this.selected)
        console.log('Релокейт: ', this.relocate)
        console.log('Скилы: ', this.skills)
        console.log('Текст: ', this.message)
        console.log('Согласен: ', this.agree)
        console.groupEnd()
      }
    },
    changeMySelect (evt) {
      this.selected = evt.target.value
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
  },
  mounted () {
    // const parser = require('xml2json')
    // const xml = '<foo attr="value">bar</foo>'
    // const json = parser.toJson(xml)
    // console.log('to json -> %s', json)
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

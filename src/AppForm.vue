<template>
    <form class="card card-w30" @submit.prevent="setSubmitted">
        <div class="form-control">
            <label for="type">Тип блока</label>
            <select id="type" v-model="typeBlock">
                <option value="title">Заголовок</option>
                <option value="subtitle">Подзаголовок</option>
                <option value="avatar">Аватар</option>
                <option value="text">Текст</option>
            </select>
        </div>

        <div class="form-control">
            <label for="value">Значение</label>
            <textarea id="value" v-model="textValue" rows="3"></textarea>
        </div>

        <button type="submit" class="btn primary" :disabled="isBtnDisabled">
            Добавить
        </button>
    </form>
</template>

<script>
export default {
  emits: {
    submitForm (element) {
      if (element) {
        return true
      }
      console.warn('Нет параметра element для emit submitForm')
      return false
    }
  },
  data () {
    return {
      textValue: '',
      typeBlock: 'title'
    }
  },
  methods: {
    setSubmitted () {
      if (this.isBtnDisabled) {
        return false
      }
      this.$emit('submitForm', {
        type: this.typeBlock,
        content: this.textValue
      })
      this.textValue = ''
      this.typeBlock = 'title'
    }
  },
  computed: {
    isBtnDisabled () {
      return this.textValue.length <= 3
    }
  }
}
</script>

<style>
</style>

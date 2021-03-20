<template>
    <div class="container column">
        <app-form @submitForm="addMarkup"></app-form>
        <div class="card card-w70">
            <h3 v-if="isDefaultMarkup">
                Добавьте первый блок, чтобы увидеть результат
            </h3>
            <app-markup
                v-else
                v-for="cvElement in cvMarkupArray"
                :cvElement="cvElement"
                :key="cvElement"
            ></app-markup>
        </div>
    </div>
    <app-comments></app-comments>
</template>

<script>
import AppForm from './AppForm'
import AppMarkup from './AppMarkup'
import AppComments from './AppComments'
export default {
  data () {
    return {
      cvMarkupArray: []
    }
  },
  methods: {
    addMarkup (element) {
      // console.log(element)
      this.cvMarkupArray.push(element)
    }
  },
  computed: {
    isDefaultMarkup () {
      return !this.cvMarkupArray || this.cvMarkupArray.length === 0
    }
  },
  components: { AppForm, AppMarkup, AppComments }
}
</script>

<style>
.avatar {
    display: flex;
    justify-content: center;
}

.avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
}
</style>

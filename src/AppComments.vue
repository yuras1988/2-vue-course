<template>
    <div class="container">
        <p v-if="!hasComments">
            <button class="btn primary" @click.once="getComments">
                Загрузить комментарии
            </button>
        </p>
        <div v-else class="card">
            <h2>Комментарии</h2>
            <ul class="list">
                <li
                    class="list-item"
                    v-for="comment in commentsArray"
                    :key="comment.id"
                >
                    <div>
                        <p>
                            <strong>{{ comment.email }}</strong>
                        </p>
                        <small>{{ comment.body }}</small>
                    </div>
                </li>
            </ul>
        </div>
    </div>
    <app-loader v-if="loading"></app-loader>
</template>

<script>
import AppLoader from './AppLoader'
import axios from 'axios'
export default {
  data () {
    return {
      loading: false,
      commentsArray: []
    }
  },
  methods: {
    getComments () {
      this.loading = true
      setTimeout(async () => {
        const { data } = await axios.get(
          'https://jsonplaceholder.typicode.com/comments?_limit=42'
        )
        this.commentsArray = Object.keys(data).map((key) => {
          return {
            id: key,
            ...data[key]
            // firstName: data[key].firstName
          }
        })
        this.loading = false
      }, 1000)
    }
  },
  computed: {
    hasComments () {
      return this.commentsArray && this.commentsArray.length > 0
    }
  },
  components: { AppLoader }
}
</script>

<style>
</style>

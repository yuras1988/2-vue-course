<template>
    <component :is="currentComponent" :cvElement="cvElement"></component>
</template>

<script>
import AppMarkupTitle from './AppMarkupTitle'
import AppMarkupSubtitle from './AppMarkupSubtitle'
import AppMarkupAvatar from './AppMarkupAvatar'
import AppMarkupText from './AppMarkupText'
export default {
  props: {
    cvElement: {
      type: Object,
      required: true
    }
  },
  computed: {
    currentComponent () {
      return 'app-markup-' + this.cvElement.type
    }
  },
  components: {
    AppMarkupTitle,
    AppMarkupSubtitle,
    AppMarkupAvatar,
    AppMarkupText
  }
}
</script>

<style>
</style>

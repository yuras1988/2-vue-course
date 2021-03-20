<template>
    <h2>{{ cvElement.content }}</h2>
</template>

<script>
export default {
  props: {
    cvElement: {
      type: Object,
      required: true
    }
  }
}
</script>

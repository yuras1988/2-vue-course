<template>
    <h1>{{ cvElement.content }}</h1>
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

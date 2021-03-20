<template>
    <p>
        {{ cvElement.content }}
    </p>
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

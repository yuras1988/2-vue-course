<template>
    <div class="avatar">
        <img :src="cvElement.content" />
    </div>
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

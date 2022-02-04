<template>
  <div class="goods"></div>
</template>

<script>
export default {
  name: 'goods',
  props: {
    data: {
      type: Object,
      default() {
        return {}
      }
    }
  }
}
</script>

<style lang="stylus" scoped></style>

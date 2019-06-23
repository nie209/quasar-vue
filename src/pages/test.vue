<template lang="html">
  <div class="row">
    <q-btn color="teal" @click="myLoading" label="Show Loading" />
  </div>
</template>

<script>
export default {
  methods: {
    myLoading () {
      console.log('calling')
    }
  }
  // methods: {
  //   myLoading () {
  //     this.$q.loading.show({
  //       message: 'Some important <b>process</b> is in progress.<br/><span class="text-primary">Hang on...</span>'
  //     })
  //
  //     // hiding in 3s
  //     this.timer = setTimeout(() => {
  //       this.$q.loading.hide()
  //       this.timer = void 0
  //     }, 3000)
  //   }
  // }
}
</script>

<style lang="css" scoped>
</style>

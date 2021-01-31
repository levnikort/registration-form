<template>
  <div class="container">
    <SingUp/>
  </div>
</template>

<script>
import SingUp from '@/components/Form/Place/SingUp'

export default {
  components: {
    SingUp
  }
}
</script>

<style lang="scss">
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100vh;
  }
</style>

<template>
    <div :class="`position-${position}`" class="d-flex justify-content-center align-items-center Loader">
      <div class="text-center">
        <Spinner :width="80" :height="80" :color="'#FEC900'" :widthStroke="6"></Spinner>
        <h2 class="text-warning mt-3 w-100">Пожалуйста подождите...</h2>
      </div>
    </div>
</template>

<script>
import Spinner from '@/components/Icons/Spinner'
export default {
  props: {
    position: {
      type: String,
      default: 'fixed'
    }
  },
  components: { Spinner },
}
</script>

<style scoped>
  .Loader {
    top: 0; 
    left: 0; 
    width: 100%; 
    height: 100%; 
    background: rgb(255 255 255 / 75%);
    z-index: 1000;
  }
</style>
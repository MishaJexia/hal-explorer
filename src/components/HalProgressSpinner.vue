<template>
  <div class="overlay" v-bind:style="overlayStyle">
    <div class="spinner">
      <md-progress-spinner
        :md-diameter="100"
        :md-stroke="10"
        md-mode="indeterminate"
      ></md-progress-spinner>
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
  name: 'HalProgressSpinner',
  computed: {
    ...mapState({
      overlayStyle: (state) => ({
        display: state.loader.isLoading ? 'block' : 'none'
      })
    })
  }
};
</script>

<style scoped>
.overlay {
  position: fixed;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 1000;
}
.spinner {
  position: absolute;
  text-align: center;
  z-index: 10000;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}
</style>

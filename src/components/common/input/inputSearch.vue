<template>
  <div class="input-wrapper">
    <!-- <slot/> -->
    <img src="@img/search-gray.svg" alt="" class="serch-image">
    <input class="input" type="text" :placeholder="placeholder">
  </div>
</template>

<script>
export default {
  name: 'input-component',
  props: ['placeholder'],
  data () {
    return {

    }
  }
}
</script>

<style lang="scss" scoped>
@import "../../../assets/styles/varibles.scss";

.input {
  width: calc(100% - 84px); // 100% - padding и еще чуть ибо криво
  height: 25px;
  padding: 12px 18px 12px 64px;
  font-size: 17px;
  outline: none;
  border: 1px solid $color-border;
  border-radius: 3px;
  // border-bottom: none;
}
.input:hover {
  outline: none;
}
.serch-image {
  position: absolute;
  width: 16px;
  margin-top: 17px;
  margin-left: 31px;
  // top: 0;
  // fill: black;
}
</style>

<template>
  <div class="input-wrapper">
    <input class="user-input" :class="{'user-input-invalid': !valid}" :type="type || 'text'" v-model="userInput" :placeholder="placeholder" @keypress.enter="emitEnter($event)" @blur="checkValidAndSetParent(userInput)">
    <label class="input-label" for="custom-input"><slot/></label>
    <span class="input-alert" v-show="!valid">{{ errorMessage }}</span>
  </div>
</template>

<script>
export default {
  name: 'input-component',
  props: ['placeholder', 'validType', 'type', 'name', 'pressEnterEmit', 'setMessage'],
  data () {
    return {
      userInput: '',
      valid: false,
      errorMessage: '',
      showMsg: false
    }
  },
  watch: {
    setMessage (newVal, oldVal) {
      if (newVal !== undefined) {
        this.showMsg = newVal.showMsg
        this.errorMessage = newVal.msg
      }
    }
  },
  methods: {
    checkValidAndSetParent (data) {
      let _valid = this.checkValid(data)
      this.$emit('setValue', {value: data, valid: _valid, name: this.name})
    },
    checkValid (data) {
      return true
    },
    emitEnter (e) {
      e.target.blur()
      this.$emit(this.pressEnterEmit)
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../../../assets/styles/varibles.scss";
.input-wrapper {
  height: 66px;
}
.user-input-invalid {
  border: 1px solid $color-accent-text;
}
.user-input {
  width: calc(100% - 38px); // 100% - padding - border
  // height: 40px;
  padding: 12px 18px;
  border: 1px solid $color-border;
  border-radius: 3px;
  font-size: 14px;
  outline: none;
  margin-top: 25px;
}
.input-label {
  position: relative;
  top: -65px;
  font-size: 14px;
  color: $color-text;
}
.input-label::before {
  display: none;
}
.input-alert {
  position: absolute;
  margin-top: -62px;
  margin-left: 9px;
  color: $color-accent-text;
  font-size: 13px;
  text-align: right;
  width: 240px;
}
</style>

<template>
  <div>
    <input type="text" :value="currentValue" @input="handleInput" @blur="handleBlur">
  </div>
</template>

<script>
export default {
  name: 'input',
  props: {
    value: {
      type: String
    }
  },
  data () {
    return {
      currentValue: this.value
    }
  },
  methods: {
    handleInput (event) {
      const value = event.target.value
      this.currentValue = value
      this.$emit('input', value)
      this.dispatch('wFormItem', 'on-from-change', value)
    },
    handleBlur () {
      this.dispatch('wFormItem', 'on-form-blur', this.currentValue)
    }
  }
}
</script>

<style scoped>

</style>

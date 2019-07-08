<template>
  <div>
    <label>{{label}}</label>
    <div>
      <solt></solt>
    </div>
  </div>
</template>

<script>
import Emitter from '@/mixins/Emitter.js'
import AsyncValidator from 'async-validator '
export default {
  name: 'wFormItem',
  inject: ['form'],
  mixins: [Emitter],
  props: {
    label: {
      type: String,
      default: ''
    },
    prop: {
      type: String
    }
  },
  methods: {
    setRules () {
      this.$on('on-form-blur', this.onFileBlur)
      this.$on('on-form-change', this.onFileChange)
    }
  },
  mounted () {
    if (this.prop) {
      this.dispatch('wFrom', 'on-form-item-add', this)
      this.setRules()
    }
  },
  destroyed () {
    this.dispatch('wForm', 'on-form-item-remove', this)
  }
}
</script>

<style scoped>

</style>

<template>
  <div>
    <form>
      <solt></solt>
    </form>
  </div>
</template>

<script>
export default {
  name: 'wForm',
  props: {
    model: {
      type: Object
    },
    rules: {
      type: Object
    }
  },
  provide () {
    return {
      form: this
    }
  },
  data () {
    return {
      fields: []
    }
  },
  created () {
    this.$on('on-form-item-add', field => {
      if (this.fields) this.fields.push(field)
    })

    this.$on('on-form-item-remove', field => {
      if (field.prop) this.fields.splice(this.fields.indexOf(field), 1)
    })
  }
}
</script>

<style scoped>

</style>

<template>
  <div class="field">
    <div class="control">
      <label class="label" :for="this.name">{{ this.placeholder }}</label>
      <input
        :id="id"
        :type="type"
        ref="input"
        :name="name"
        @input="$emit('input', $event.target.value);"
        class="input"
        :class="{ 'is-danger': error }"
        :placeholder="placeholder"
      />
      <small v-if="error" class="field-text error">{{ error }}</small>
    </div>
  </div>
</template>

<script>
export default {
  name: 'text-input',
  $_veeValidate: {
    value() {
      return this.$el.value
    },
    name() {
      return this.name
    }
  },
  props: {
    name: String,
    value: {
      type: null,
      default: null
    },
    error: {
      type: String,
      default: null
    },
    placeholder: {
      type: String,
      default: null
    },
    id: {
      type: String,
      default: null
    },
    type: {
      type: String,
      default: 'text'
    }
  },
  mounted() {
    this.$refs.input.value = this.value
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/main.scss';

.label {
  cursor: pointer;
  text-transform: capitalize;
}
.error {
  color: $red;
}
</style>
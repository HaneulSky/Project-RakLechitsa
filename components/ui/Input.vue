<template>
  <input
    :class="['input', className]"
    :type="type"
    :placeholder="placeholder"
    :name="name"
    :required="required"
    v-model="content"
    @input="handleInput"
  />
</template>

<script>
export default {
  props: {
    type: String,
    placeholder: String,
    name: String,
    required: Boolean,
    className: String,
    value: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      content: this.value,
    };
  },
  watch: {
    value(newVal) {
      if (newVal !== this.content) {
        this.content = newVal;
      }
    },
  },
  methods: {
    handleInput(content) {
      this.$emit('input', this.content);
    },
  },
};
</script>

<style scoped>
.input {
  width: 100%;
  border: 1px solid #e8e8e8;
  height: 24px;
  padding: 5px;
  font-size: 14px;
  box-sizing: border-box;
  font-size: 18px;
  line-height: 24px;
}
</style>

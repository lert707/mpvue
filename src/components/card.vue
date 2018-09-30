<template>
  <div>
    <p class="card">
      456
      {{text}}
    </p>
    <input class="input" v-model="inputValue" type="text" @input="test">
  </div>
</template>

<script>
export default {
  props: {
    text: {
      type: String
    }
  },
  data() {
    return {
      inputValue: ""
    }
  },
  watch: {
    inputValue(newValue, oldValue) {
      console.log(newValue, 333)
    },
  },
  methods: {
    test() {
      this.$emit("getMsg", this.inputValue)
    }
  },
  onShow() {
    console.log(this.text, "组件")
  }
}
</script>

<style>
.card {
  padding: 10px;
}
.input {
  border: 1px solid #000;
}
</style>

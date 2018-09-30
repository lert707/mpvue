<template>
  <div class="counter-warp">
    <div>other</div>
    <span @click="sub">-</span>
    <span>{{num}}</span>
    <span @click="add">+</span>
    <div>{{price}}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num: 0
    };
  },
  computed: {
    price() {
      return this.num * 300;
    }
  },
  methods: {
    add() {
      this.num++;
    },
    sub() {
      this.num--;
    }
  },
  created() {},
  mounted() {
    console.log(this.$root.$mp.query);
  }
};
</script>

<style scoped>
</style>

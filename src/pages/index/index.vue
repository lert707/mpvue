<template>
  <div class="container">
    <div>123465</div>
    <div>hello world</div>
    <div v-for="item in list" :key="item.id" @click="test(item)">
      {{item.username}}: {{item.openid}}
    </div>
    <div v-for="item in list" :key="item.id" @click="test(item)">
      {{item.username}}: {{item.openid}}
    </div>
    <div v-for="item in list" :key="item.id" @click="test(item)">
      {{item.username}}: {{item.openid}}
    </div>
    <div v-for="item in list" :key="item.id" @click="test(item)">
      {{item.username}}: {{item.openid}}
    </div>
    <input class="input" type="text">
    <div class="usermotto">
      <div class="user-motto">
        <card :text="motto" @getMsg="getMsg"></card>
      </div>
    </div>
    <button @click="toMy">点我去我的页面</button>
  </div>
</template>

<script>
import card from "@/components/card";

export default {
  data() {
    return {
      motto: "Hello World",
      list: []
    };
  },

  components: {
    card
  },

  methods: {
    getData() {
      wx.request({
        url: "http://127.0.0.1:3000/api/getAll",
        success: res => {
          console.log(res)
          this.list = res.data.data;
        },
        fail: () => {},
        complete: () => {}
      });
      wx.login({
        success: res => {
          console.log(res);
        },
        fail: () => {},
        complete: () => {}
      });
    },
    test(item) {
      // console.log(item);
      wx.navigateTo({
        url: "/pages/other/main?username=admin&password=admin"
      });
    },
    getMsg(msg) {
      // console.log(msg);
    },
    toMy() {
      wx.switchTab({ url: "/pages/my/main" });
    }
  },
  onPullDownRefresh() {
  },

  onReachBottom() {
    console.log("触底了");
  },

  created() {
    this.getData();
  }
};
</script>

<style scoped>
.input {
  border: 1px solid #000;
}
</style>

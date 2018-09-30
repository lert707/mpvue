<template>
  <div class="counter-warp">
    <view class="user">
      <open-data type="userAvatarUrl" class="usericon"></open-data>
      <open-data type="userNickName" class="username"></open-data>
    </view>
    <button open-type="getUserInfo" @click="getinfo">获取用户信息</button>
    <card :text="desc"></card>
  </div>
</template>

<script>
import card from "@/components/card";

export default {
  data() {
    return {
      desc: "this is my"
    };
  },
  components: {
    card
  },
  computed: {},
  methods: {
    getinfo() {
      wx.getUserInfo({
        withCredentials: false,
        success: res => {
          console.log(res);
        },
        fail: () => {},
        complete: () => {}
      });
    }
  },
  mounted() {
    // this.getinfo()
  },
  onShow() {
    this.getinfo();
  },
  onLoad() {
    console.log("load");
  }
};
</script>

<style scoped lang="less">
.user {
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  .usericon {
    width: 220rpx;
    height: 220rpx;
    display: flex;
    border-radius: 50%;
    overflow: hidden;
    margin: 20rpx;
  }
}
</style>

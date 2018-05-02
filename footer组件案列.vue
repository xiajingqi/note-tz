<template>
  <div class="footer">
    <div v-for="item in items" :key="item.id" @click="to(item)" class="footer-item" :class="{active: current==item.id}">
      <img :src="'/static/images/icon-'+(item.icon+(current==item.id ? '-active' : ''))+'.png'">
      <p>{{item.text}}</p>
    </div>
  </div>
</template>
<script>
import navigateTo from '@/utils/navigator';
export default {
  name: 'footer',
  props: ['current'], //当前选中tab，1 首页 2 消息 3 我的
  data() {
    return {
      items: [
        {
          id: 1,
          text: '首页',
          icon: 'home',
          target: 'index'
        },
        {
          id: 2,
          text: '消息',
          icon: 'chat',
          target: 'index'
        },
        {
          id: 3,
          text: '我',
          icon: 'me',
          target: 'my'
        }
      ]
    };
  },
  methods: {
    to({ id, target }) {
      // if(){
      //   相当于
      // }
      id != this.current && navigateTo(target, {}, true);
    }
  }
};
</script>
<style scoped>
.footer {
  position: fixed;
  bottom: 0;
  width: 750rpx;
  height: 98rpx;
  display: flex;
  justify-content: space-around;
  background: #fff;
  border-top: 1px solid #bdc6cf;
}
.footer-item {
  text-align: center;
  position: relative;
  padding-top: 18rpx;
}
.footer-item img {
  width: 44rpx;
  height: 44rpx;
}
.footer-item p {
  font-size: 20rpx;
  color: #8a8a8c;
  line-height: 10rpx;
}
.footer-item.active p {
  color: #3073f4;
}
</style>

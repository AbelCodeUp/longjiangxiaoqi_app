<template>
  <ul v-if="list.length">
    <router-link
      tag="li"
      :to="{path: 'jobs', query:{id: item.id}}"
      v-for="item in list"
      :key="item.id"
      class="list-item"
    >
      <img class="item-logo" :src="item.logo" />
      <div class="item-desc">
        <h3 class="item-title">{{ item.name }}</h3>
        <p class="item-info">
          <span style="display:none" class="item-pos">{{ item.province }}【{{item.area}}】</span>
          <span>{{item.moneyMin}} -{{item.moneyMax}} k</span>
          <span class="eduName">{{item.eduName}}</span>
          <span>{{ item.workExpName }}年</span>
          <span class="item-salary">{{ item.publishedTime }}</span>
        </p>
        <p class="item-time">{{ item.province }}【{{item.area}}】</p>
      </div>
    </router-link>
    <!-- <li class="list-more" @click="loadMore()">加载更多</li> -->
  </ul>
</template>

<script>
export default {
  name: "jobList",
  data: () => ({
    pageNo: 1
  }),
  props: ["list"],
  mounted(){
    this.dataList();
  },
  methods: {
    // loadMore: function() {
    //   this.$emit("loadMore", ++this.pageNo);
    // },
    dataList() {
      // console.log(this.list);
    }
  }
};
</script>

<style lang="less">
@import "../style/mixin";

.list-item {
  .activeBg;
  padding: 14px;
  border-bottom: 1px solid #e8e8e8;
}
.item-logo {
  display: inline-block;
  float: left;
  width: 60px;
  height: 60px;
}
.item-desc {
  margin-left: 70px;
  height: 62px;
  color: #333;
}
.item-title {
  font-size: 1.4rem;
  font-weight: bold;
  margin-bottom: 6px;
  width: 80%;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
.item-info {
  margin-bottom: 6px;
  width: 100%;
  height: 15px;
  line-height: 15px;
}
.item-pos {
  font-size: 1.1rem;
  float: left;
  width: 60%;
  display: inline-block;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
.item-salary {
  font-size: 1.2rem;
  color: #00b38a;
  float: right;
}
.item-time {
  font-size: 0.9rem;
  color: #888;
}
.list-more {
  height: 50px;
  line-height: 50px;
  text-align: center;
  font-size: 1.2rem;
  &:active {
    background-color: #f0f0f0;
  }
}
.eduName{
  margin-left:1rem;

}
</style>

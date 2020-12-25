<template>
  <div class="middle">
    <div class="head">
      <div class="left">店铺宝贝</div>
      <div class="right">
        <span style="width:54px;">积分</span>
        <span style="width:82px;">单价(元)</span>
        <span style="width:104px;">数量</span>
      </div>
    </div>
    <ul class="content">
      <li class="shop-content" v-for="(item,index) in title" :key="index">
        <div class="shop-info">
          <p>店铺：<span>{{item.shopper}}</span> 卖家：<span>{{item.master}}</span></p>
          <img src="../../static/image/taobao_relation.jpg" alt="" />
        </div>
        <div class="shop-list" v-for="(item1,index1) in item.data" :key="index1">
          <ul class="left">
            <li>
              <img
                :src="item1.image"
                alt=""
                style="width: 100px; height: 100px"
              />
            </li>
            <li class="shop" style="flex-grow: 1">
              <a href="#">{{item1.title}}</a>
              <p v-show = "item1.style">
                <span v-for="(i,j) in item1.style" :key="j" style ="margin-right:8px;">{{i}}</span>
              </p>
              <p>
                保障：<img src="../../static/image/taobao_icon_01.jpg" alt="" />
              </p>
            </li>
          </ul>
          <div class="right">
            <div style="width:54px;">{{item1.score}}</div>
            <div style="width:82px;">{{item1.price}}</div>
            <div style="width:104px;">
              <img src="../../static/image/taobao_minus.jpg" alt="" @click="minus(item1)"/>
              <input type="text" v-model.number = "item1.num"/>
              <img src="../../static/image/taobao_adding.jpg" alt="" @click="add(item1)" />
            </div>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: Array,
      default: ()=>[]
    },
  },
  methods: {
    minus(item) {
      this.$emit("change",{
        type:"minus",
        item
      })
    },
    add(item){
      this.$emit("change",{
        type:"add",
        item
      })
    }
  },
};
</script>

<style lang="scss" scoped>
.middle {
  .head {
    display: flex;
    .left {
      width: 80%;
      text-align: center;
    }
    .right {
      width: 20%;
      display: flex;
      align-items: center;

      span {
        display: block;
        text-align: center;
      }
    }
  }
}
.content {
  padding: 0;
  list-style: none;
}
.shop-content {
  margin-top: 10px;
}
.shop-info {
  display: flex;
  p {
    margin: 0;
    span {
      margin: 0 4px;
    }
  }
}
.shop-list {
  display: flex;
  margin: 4px 0;
  .left {
    padding: 0;
    width: 80%;
    display: flex;
    list-style: none;
    &.img {
      width: 100px;
      height: 100px;
    }
    li {
      padding: 10px 20px;
      background-color: rgb(150, 205, 226);
      margin-right: 4px;
      &.shop {
        flex-grow: 1;
        height: 100%;
        display: flex;
        box-sizing: border-box;
        flex-direction: column;
        justify-content: space-between;
        a {
          text-decoration: none;
          &:hover {
            color: red;
          }
        }
      }
    }
  }
  .right{
    display: flex;
    align-items: center;
    input{
      width: 20px;
      border:1px solid skyblue;
      outline: none;
      text-align: center;
    }
    img{
      width: 20px;
      cursor: pointer;
    }
    div{
      display: flex;
      height: 100%;
      align-items: center;
      justify-content: center;
      background: rgb(150, 205, 226);
      margin-right: 4px;
      text-align: center;
      &:last-of-type{
        margin-right: 0;
      }
    }
    
  }
}
</style>
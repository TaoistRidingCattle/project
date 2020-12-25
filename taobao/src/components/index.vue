<template>
  <div>
    <Header></Header>
    <Middle :title = "list" @change="shopnumChange"></Middle>
    <Footer :title = "list" @clear ="clear"></Footer>
  </div>
</template>

<script>
import Header from "./header";
import Middle from "./middle";
import Footer from "./footer";
export default {
  data() {
    return {
      list: [],
    };
  },
  methods: {
      shopnumChange(obj) {
          switch(obj.type){
              case 'minus':
                  if(obj.item.num>1){
                      obj.item.num--
                  }
                  else {
                      obj.item.num = 1
                  }
                  break;
              case 'add':
                  if(obj.item.num<10){
                      obj.item.num++
                  }
                  else {
                      obj.item.num = 10
                  }
                  break;
          }
      },
      clear(){
          this.list = []
      }
  },
  components: {
    Header,
    Middle,
    Footer,
  },
  created() {
    this.list = [
      {
        shopper: "纤巧百媚时尚鞋坊",
        master: "纤巧百媚",
        data: [
          {
            title: "日韩流行风时尚美眉最爱独特米字拼图金属坡跟公主靴子黑色",
            image: require("../../static/image/taobao_cart_01.jpg"),
            style: {
              color: "颜色：棕色",
              size: "尺寸：37",
            },
            score: 6,
            price: 100,
            num: 1,
          },
          {
            title: "chanel/香奈尔/香奈尔炫亮魅力唇膏3.5g ",
            image: require("../../static/image/taobao_cart_02.jpg"),
            score: 12,
            price: 265,
            num: 1,
          },
        ],
      },
      {
        shopper: "香港我的美丽日记",
        master: "taobao豆豆",
        data: [
          {
            title: "相宜促销专供 大S推荐 最好用的LilyBell化妆棉 好用/推荐/ ",
            image: require("../../static/image/taobao_cart_03.jpg"),
            score: 10,
            price: 100,
            num: 1,
          },
        ],
      },
    ];
  },
};
</script>

<style lang="scss" scoped>
</style>
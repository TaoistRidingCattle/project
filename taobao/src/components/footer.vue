<template>
  <div class="footer">
    <div class="all-price">
        <span>商品总价(不含运费)：</span>
        <p><span>{{total}}</span>元</p>
    </div>
    <a href="javascript:;" @click ="change">清空购物车</a>
    <div class="score">
        <p>可获积分<span>{{score}}</span>点</p>
        <img src="../../static/image/taobao_subtn.jpg" alt="">
    </div>
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
    data() {
        return {
            list: []
        }
    },
    methods: {
        change() {
            this.$emit("clear")
        }
    },
    computed: {
        total(){
            return this.title.reduce((sum,item)=>{
                return sum + item.data.reduce((sum1,item1)=>{
                    return sum1 + item1.price*item1.num
                },0)
            },0)
        },
        score(){
            return this.title.reduce((sum,item)=>{
                return sum + item.data.reduce((sum1,item1)=>{
                    return sum1 + item1.score
                },0)
            },0)
        }
    
    },
};
</script>
<style lang="scss" scoped>
.footer{
    a{
        text-decoration: none;
        &:hover{
            color:red;
        }
    }
}
.all-price{
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    p{
        margin: 0 ;
        margin-right: 20px;
        span{
            color:#ff6600;
            font-size: 30px;
            margin-right: 4px;
        }
    }
}
.score{
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    margin-right: 20px;
    p{
        
        span{
            color:#ff6600;
            font-size: 30px;
            margin-right: 4px;
        }

    }
}
</style>
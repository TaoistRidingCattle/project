<template>
  <div class="header">
    <img :src="img" alt="" />
    <div>
        您的位置：
        <span><a href="javascript:;" >首页</a></span>
        &gt;
        <span><a href="javascript:;">我的淘宝</a></span>
        &gt;
        <span><a href="javascript:;" class="active">我的购物车</a></span>
    </div>
    <ul>
        <li class="first active">1.查看购物车</li>
        <li class="noActive">2.确认订单信息</li>
        <li class="noActive">3.付款到支付宝</li>
        <li class="noActive">4.确认收货</li>
        <li class="noActive last">5.评价</li>
    </ul>
  </div>
</template>

<script>
    import img from "../../static/image/taobao_logo.gif"
    export default {
        data() {
            return {
                img
            }
        },
    }
</script>

<style lang="scss" scoped>

.header {
    span{
        margin: 0 4px;
        a{
            text-decoration: none;
            &:hover{
                color:red;
            }
            &.active {
                color:#444;
                &:hover{
                    color:rgb(240, 99, 99);
                }
            }
        }
    }
    ul{
        list-style: none;
        padding: 0;
        display: flex;
        li{
            background: #e4e4e4;
            flex-grow: 1;
            text-align: center;
            height: 23px;
            line-height: 23px;
            position: relative;
            &.active{
                background: #ff6600;
                color: #fff;
            }
            &.first::before{
                content: '';
                background: url("../../static/image/taobao_bg.png") no-repeat;
                position: absolute;
                left:-15px;
                top:0;
                width: 15px;
                height: 23px;
                background-position: 0 -92px;
            }
            &.active:not(:last-of-type):after{
                content: '';
                background: url("../../static/image/taobao_bg.png") no-repeat;
                position: absolute;
                right:0px;
                top:0;
                width: 15px;
                height: 23px;
                background-position: 0 0px;
            }
            &.noActive:not(:last-of-type)::after{
                content: '';
                background: url("../../static/image/taobao_bg.png") no-repeat;
                position: absolute;
                right:0px;
                top:0;
                width: 15px;
                height: 23px;
                background-position: 0 0px;
            }
            &.last::after{
                content: '';
                background: url("../../static/image/taobao_bg.png") no-repeat;
                position: absolute;
                right:0px;
                top:0;
                width: 15px;
                height: 23px;
                background-position: 0 -138px;
            }
        }
    }
}
</style>
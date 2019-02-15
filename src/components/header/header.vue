<template>
    <div class="header">
        <div class="content-wrapper">
            <div class="avatar">
                <img :src="seller.avatar" />
            </div>
            <div class="content">
                <div class="title">
                    <span class="brand"></span>
                    <span class="name">{{ seller.name }}</span>
                </div>
                <div class="description">
                    {{ seller.description }}/{{ seller.deliveryTime }}分钟送达
                </div>
                <div class="support" v-if="seller.supports"> <!-- 需要加判断，如没有的话在下面取数组0会报错 -->
                    <span class="icon" :class="classMap[seller.supports[0].type]"></span>
                    <span class="text">{{ seller.supports[0].description }}</span>
                </div>
            </div>
            <div class="support-count" v-if="seller.supports">
                <span class="count">{{ seller.supports.length }}个</span>
                <span class="icon-keyboard_arrow_right"></span>
            </div>
        </div>
        <div class="bulletin-wrapper">
            <span class="bulletin-icon"></span>
            <span class="bulletin-text">{{ seller.bulletin }}</span>
            <span class="icon-keyboard_arrow_right"></span>
        </div>
        <div class="background">
            <img :src="seller.avatar" width="100%" height="100%"/>
        </div>
    </div>
</template>

<script>
export default {
    name : "Header",
    data() {
        return {

        }
    },
    props: {
        seller : Object
    },
    created() {
        this.classMap = ["decrease", "discount", "special", "invoice", "guarantee"];
    }
}
</script>

<style lang="stylus" scoped>
    @import "../../common/stylus/mixin.styl"

    .header
        position : relative
        color : #ffffff
        background : rgba(7, 17, 27, 0.5)
        overflow : hidden  // 模糊效果会影响超出部分
        .content-wrapper
            position : relative
            padding : .48rem .24rem .36rem .48rem
            color : #ffffff
            .avatar
                display : inline-block
                border-radius : .04rem
                vertical-align : top
                img 
                    width : 1.28rem
                    height : 1.28rem
            .content
                display : inline-block
                margin-left : .32rem
                .title
                    margin : .04rem 0 .16rem 0
                    .brand 
                        display : inline-block
                        width : .6rem
                        height : .32rem
                        bg-image("images/brand")
                        background-size : .6rem .32rem
                        backgroundrepeat : no-repeat
                    .name
                        margin-left : .12rem
                        font-size : .32rem
                        font-weight : bold
                        line-height : .36rem
                        vertical-align : top
                .description
                    margin-bottom : .2rem
                    font-size : .24rem
                    font-weight : 200
                    line-height : .24rem
                .support
                    .icon
                        display : inline-block
                        width : .24rem
                        height : .24rem
                        margin : 0 .08rem .04rem 0
                        vertical-align : top
                        background-size : .24rem .24rem
                        background-repeat : no-repeat
                        &.decrease
                            bg-image("images/decrease_1")
                        &.discount
                            bg-image("images/discount_1")
                        &.guarantee
                            bg-image("images/guarantee_1")
                        &.invoice
                            bg-image("images/invoice_1")
                        &.special
                            bg-image("images/special_1")
                    .text
                        font-size : .2rem
                        line-height : .24rem
                        font-weight : 200
            .support-count  
                position : absolute
                bottom : .36rem
                right : .24rem
                padding : 0 .16rem
                height : .48rem
                line-height : .48rem
                border-radius : .28rem  
                background-color : rgba(0, 0, 0, .2)
                .count
                    font-size : .2rem
                    vertical-align : top
                .icon-keyboard_arrow_right
                    margin-left : .04rem
                    line-height : .24rem
                    font-size : .2rem
        .bulletin-wrapper
            position : relative
            height : .56rem
            line-height : .56rem
            padding : 0 .24rem
            background-color : rgba(7, 17, 27, 0.2)
            color : #ffffff
            overflow : hidden
            text-overflow : ellipsis  
            white-space : nowrap  
            .bulletin-icon
                display : inline-block
                width : .44rem
                height : .24rem
                margin-right : .08rem
                vertical-align : top
                margin-top : .16rem
                bg-image("images/bulletin")
                background-size : .44rem .24rem
                background-repeat : no-repeat
            .bulletin-text
                font-size : .2rem
                font-weight : 200
                vertical-align : top
            .icon-keyboard_arrow_right
                position : absolute 
                right : .24rem
                top : .18rem
                margin-left : .08rem
                line-height : .24rem
                font-size : .2rem
        .background
            position : absolute 
            left : 0
            top : 0
            z-index : -1
            width : 100%
            height : 100%
            filter : blur(.1rem)



                
                    





</style>

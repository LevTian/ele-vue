<template>
    <div class="header">
        <div class="content-wrapper">
            <div class="avatar">
                <img width="64" height="64" :src="seller.avatar" />
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
                    <span class="icon">{{ seller.supports[0].type }}</span>
                    <span class="text">{{ seller.supports[0].description }}</span>
                </div>
            </div>
        </div>
        <div class="bulletin-wrapper"></div>
        
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
    }
}
</script>

<style lang="stylus" scoped>
    @import "../../common/stylus/mixin.styl"

    .header
        color : #ffffff
        background : #cccccc
        .content-wrapper
            padding : .48rem .24rem .36rem .48rem
            .avatar
                display : inline-block
            .content
                display : inline-block
                margin-left : .32rem
                .title
                    margin : .4rem 0 .16rem 0
                    
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
                    line-height : 24px

</style>

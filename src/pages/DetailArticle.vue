<!-- 文章详情 -->
<template>
    <div>
        <brand></brand>
        <zac-nav></zac-nav>
        <div  class="container" id="detail">
            <el-row  :gutter="30">
                <el-col :sm="24" :md="16" style="transition:all .5s ease-out;margin-bottom:30px;">
                    <zac-articleDetail></zac-articleDetail>
                    <zac-message></zac-message>
                </el-col>
                <el-col :sm="24"  :md="8" >
                    <zac-rightlist></zac-rightlist>
                </el-col>
            </el-row>
        </div>
    </div>
</template>

<script>
import Brand from '../components/brand.vue';
import header from '../components/header.vue'
import rightlist from '../components/rightlist.vue'
import articleDetail from '../components/articleDetail.vue'
import message from '../components/message.vue'
    export default {
        name:'DetailShare',
        data() { //选项 / 数据
            return {

            }
        },
        methods: { //事件处理器

        },
        components: { //定义组件
            'brand': Brand,
            'zac-nav':header,
            'zac-articleDetail':articleDetail,
            'zac-message':message,
            'zac-rightlist':rightlist,
        },
        created() { //生命周期函数

        },
        mounted(){
            var anchor = document.querySelector("#detail");
            // console.log(anchor,anchor.offsetTop);
            var top = anchor.offsetTop-60;
            document.body.scrollTop = top;
             // Firefox
             document.documentElement.scrollTop = top;
             // Safari
             window.pageYOffset = top;
        }
    }
</script>

<style>
</style>

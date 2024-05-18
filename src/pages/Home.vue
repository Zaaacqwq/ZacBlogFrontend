<!-- 首页 -->
<template>
    <div>
        <image-carousel></image-carousel>
        <brand></brand>
        <background></background>
        <zac-navbar></zac-navbar>
        <div class="container">
            <el-row :gutter="30">
                <el-col :sm="24" :md="16" style="transition:all .5s ease-out;margin-bottom:30px;">
                    <zac-articlelist></zac-articlelist>
                </el-col>
                <el-col :sm="24" :md="8">
                    <zac-rightlist></zac-rightlist>
                </el-col>
            </el-row>
        </div>
    </div>
</template>

<script>
import Images from '../components/images.vue';
import Brand from '../components/brand.vue';
import Background from '../components/background.vue';
import header from '../components/header.vue'
import articlelist from '../components/articlelist.vue'
import rightlist from '../components/rightlist.vue'
export default {
    name: 'Home',
    data() { //选项 / 数据
        return {

        }
    },
    methods: { //事件处理器

    },
    components: { //定义组件
        'image-carousel': Images,
        'brand': Brand,
        'zac-navbar': header,
        'background': Background,
        'zac-articlelist': articlelist,
        'zac-rightlist': rightlist,
    },
    created() { //生命周期函数

    }
}
</script>

<style>

</style>
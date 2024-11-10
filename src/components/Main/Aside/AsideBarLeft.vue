<template>
    <div style="display: flex; justify-content: center; align-items: center">
        <el-button
            text
            circle
            :icon="isCollapse ? ArrowLeft : ArrowRight"
            @click="isCollapse = !isCollapse"
        ></el-button>
    </div>
    <div class="aside-bar-left">
        <el-menu :collapse="isCollapse" class="temp-menu-class">
            <template v-for="(item, index) in asideData.data" :key="index" :index="index">
                <template v-if="item.subGroup.length === 0">
                    <el-menu-item>
                        <el-icon><component :is="item.icon"></component></el-icon>
                        <span>{{ item.title }}</span>
                    </el-menu-item>
                </template>
                <template v-else>
                    <el-sub-menu :index="item.index">
                        <template #title>
                            <el-icon><component :is="item.icon"></component></el-icon>
                            <span>{{ item.title }}</span>
                        </template>
                        <el-menu-item-group
                            v-for="(item1, index) in item.subGroup"
                            :key="index"
                            :title="item1.title"
                        >
                            <el-menu-item
                                v-for="(subItem, index) in item1.subItem"
                                :key="index"
                                :index="subItem.index"
                            >
                                <el-icon
                                    ><component :is="subItem.icon"></component
                                ></el-icon>
                                <span>{{ subItem.title }}</span>
                            </el-menu-item>
                        </el-menu-item-group>
                    </el-sub-menu>
                </template>
            </template>
        </el-menu>
    </div>
</template>

<script>
import { ArrowLeft, ArrowRight } from '@element-plus/icons-vue';
import AsideData from '../../../staticData/AsideData.json';
export default {
    name: 'AsideBarLeft',
    data() {
        return {
            asideData: AsideData,
            isCollapse: true,
            ArrowLeft: ArrowLeft,
            ArrowRight: ArrowRight,
        };
    },
    mounted() {
        console.log(this.asideData);
        // for (let i = 0; i < this.asideData.length; i++) {
        //     console.log(this.asideData[i].index);
        // }
    },
};
</script>

<style scoped>
.aside-bar-left {
    height: 100%;
    /* background-color: #ca3232; */

    display: flex;
    /* align-items: center; */
}
.temp-menu-class:not(.el-menu--collapse) {
    width: 200px;
}
</style>

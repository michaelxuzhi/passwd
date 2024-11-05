<template>
    <div class="aside-bar-left">
        <el-menu>
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
import AsideData from '../../../staticData/AsideData.json';
export default {
    name: 'AsideBarLeft',
    data() {
        return {
            asideData: AsideData,
        };
    },
    mounted() {
        console.log(this.asideData);
        // for (let i = 0; i < this.asideData.length; i++) {
        //     console.log(this.asideData[i].index);
        // }
    },
    computed: {
        asideDataWithSubGroup() {
            const result = [];
            for (let i = 0; i < this.asideData.data.length; i++) {
                const item = this.asideData.data[i];
                if (item.subGroup.length > 0) {
                    result.push(item);
                }
            }
            return result;
        },
        asideDataWithoutSubGroup() {
            const result = [];
            for (let i = 0; i < this.asideData.data.length; i++) {
                const item = this.asideData.data[i];
                if (item.subGroup.length === 0) {
                    result.push(item);
                }
            }
            return result;
        },
    },
};
</script>

<style scoped>
.aside-bar-left {
    /* width: 100%; */
    height: 100%;
    /* background-color: #ca3232; */

    display: flex;
    justify-content: center;
    /* align-items: center; */
}
</style>

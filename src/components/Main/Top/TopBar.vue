<template>
    <div class="top-bar">
        <el-row :gutter="10">
            <el-col :xs="8" :sm="6" :md="4" :lg="3" :xl="1">
                <div class="grid-content">
                    <img
                        class="top-bar-logo"
                        src="../../../assets/flower_std_128.png"
                        alt="passwd logo"
                    />
                    <div class="top-bar-title">Passwd</div>
                </div>
            </el-col>
            <el-col :xs="4" :sm="6" :md="8" :lg="9" :xl="11">
                <div class="grid-content">
                    <div class="top-bar-search">
                        <el-input
                            v-model="top_input"
                            class="input-with-select"
                            :size="top_search_size"
                            placeholder="Please Input"
                        >
                            <template #prepend>
                                <el-select
                                    v-model="top_select"
                                    placeholder="Select"
                                    class="top-bar-select"
                                    :size="top_search_size"
                                >
                                    <el-option label="Restaurant" value="1" />
                                    <el-option label="Order No." value="2" />
                                    <el-option label="Tel" value="3" />
                                </el-select>
                            </template>
                            <template #append>
                                <el-button :icon="Search" class="icon-search"></el-button>
                            </template>
                        </el-input>
                    </div>
                </div>
            </el-col>
            <el-col :xs="4" :sm="6" :md="8" :lg="9" :xl="11">
                <div class="grid-content">
                    <div class="top-bar-func">
                        <template
                            v-for="(item, index) in navData.data"
                            :key="index"
                            :index="index"
                        >
                            <template v-if="item.type === 'dropdowngroup'">
                                <el-dropdown class="top-bar-dropdown-item">
                                    <span class="el-dropdown-link"
                                        >{{ item.title }}
                                        <el-icon v-if="item.subGroup.length > 0"
                                            ><arrow-down
                                        /></el-icon>
                                    </span>
                                    <template #dropdown v-if="item.subGroup.length > 0">
                                        <el-dropdown-menu>
                                            <el-dropdown-item
                                                v-for="subItem in item.subGroup"
                                                :key="subItem.id"
                                                :index="subItem.id"
                                                :icon="subItem.icon"
                                            >
                                                {{ subItem.title }}
                                            </el-dropdown-item>
                                        </el-dropdown-menu>
                                    </template>
                                </el-dropdown>
                            </template>
                            <template v-if="item.type === 'link'">
                                <div class="top-bar-func-link">{{ item.title }}</div>
                            </template>
                            <template v-if="item.type === 'avatar'">
                                <el-avatar :size="30" :src="circleUrl"></el-avatar>
                            </template>
                        </template>
                    </div>
                </div>
            </el-col>
            <el-col :xs="8" :sm="6" :md="4" :lg="3" :xl="1">
                <div class="grid-content">
                    <div class="top-bar-switch">
                        <el-switch
                            v-model="top_switch_value"
                            :size="top_search_size"
                            inline-prompt
                            style="
                                /* --el-switch-on-color: #c5450b; */
                                --el-switch-off-color: #c5450b;
                            "
                            active-text="亮"
                            inactive-text="暗"
                            @change="topSwitchTheme"
                        >
                        </el-switch>
                    </div>
                </div>
            </el-col>
        </el-row>
    </div>
</template>

<script>
import {
    Plus,
    CircleCheck,
    CirclePlusFilled,
    CirclePlus,
    Search,
    Check,
    Close,
} from '@element-plus/icons-vue';
import { useDark, useToggle } from '@vueuse/core';

const isDark = useDark();
const toggleDark = useToggle(isDark);

import NavData from '../../../staticData/NavData.json';
export default {
    name: 'TopBar',
    data() {
        return {
            top_input: '',
            top_select: '',
            top_search_size: 'large',
            top_switch_value: false,
            navData: [],
            Search: Search,
            Check: Check,
            Close: Close,
            Plus: Plus,
            CirclePlusFilled: CirclePlusFilled,
            CirclePlus: CirclePlus,
            CircleCheck: CircleCheck,
            circleUrl:
                'https://cube.elemecdn.com/3/7c/3ea6beec64369c2642b92c6726f1epng.png',
        };
    },
    methods: {
        topSwitchTheme() {
            toggleDark();
        },
    },
    created() {},
    mounted() {
        this.navData = NavData;
    },
};
</script>

<style scoped>
.top-bar {
    height: 50px;
    color: #c5450b;
    line-height: 50px;
}
.grid-content {
    border-radius: 4px;
    display: flex;
    /* justify-content: center;  */
    align-items: center;
}
.top-bar-logo {
    height: 50px;
    width: 50px;
}
.top-bar-title {
    font-size: 24px;
    font-weight: bold;
    padding-left: 10px;
}
.top-bar-search {
    width: 80%;
    margin-left: auto;
    border-radius: 4px;
}
.top-bar-select {
    width: 115px;
    border-radius: 4px;
}
.input-with-select {
    border-radius: 4px;
}
.top-bar-func {
    height: 50px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    margin-left: auto;
}
.top-bar-func > div {
    margin-right: 25px;
}
.top-bar-func > .el-avatar {
    margin-left: 15px;
}
.top-bar-func-link {
    font-size: 14px;
    font-weight: bold;
}
.top-bar-switch {
    margin-left: auto;
}
.top-bar-dropdown-item {
    cursor: pointer;
}
</style>

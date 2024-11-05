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
                    <div class="top_bar_func">
                        <div class="top-bar-title">文本1</div>
                        <div class="top-bar-title">文本2</div>
                        <div class="top-bar-title">文本3</div>
                        <div class="top-bar-title">文本4</div>
                        <el-avatar :size="30" :src="circleUrl"></el-avatar>
                        <el-avatar :size="30" :src="circleUrl"></el-avatar>
                        <el-avatar :size="30" :src="circleUrl"></el-avatar>
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
import { Search, Check, Close } from '@element-plus/icons-vue';
import { useDark, useToggle } from '@vueuse/core';

const isDark = useDark();
const toggleDark = useToggle(isDark);
export default {
    name: 'TopBar',
    data() {
        return {
            top_input: '',
            top_select: '',
            top_search_size: 'large',
            top_switch_value: false,
            Search: Search,
            Check: Check,
            Close: Close,
            circleUrl:
                'https://cube.elemecdn.com/3/7c/3ea6beec64369c2642b92c6726f1epng.png',
        };
    },
    methods: {
        topSwitchTheme() {
            toggleDark();
        },
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
.top_bar_func {
    height: 50px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    margin-left: auto;
}
.top_bar_func > div {
    margin-right: 15px;
}
.top_bar_func > .el-avatar {
    margin-left: 15px;
}
.top-bar-switch {
    margin-left: auto;
}
</style>

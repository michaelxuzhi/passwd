<template>
    <div class="body-content">
        <el-table :data="tableData" border style="width: 100%">
            <el-table-column prop="id" label="ID" width="100"></el-table-column>
            <el-table-column prop="name" label="Name" width="180">
                <template #default="{ row }">
                    <el-cascader
                        v-model="row.test"
                        :options="row.name"
                        :show-all-levels="false"
                        @change="handleCascaderChange(row.test, row.name)"
                    ></el-cascader>
                </template>
            </el-table-column>
        </el-table>
    </div>
</template>

<script>
import testData from '../../../staticData/testData.json';
export default {
    name: 'BodyContent',
    data() {
        return {
            tableData: [],
            initData: ['qa', 'lily'],
            initData1: 'Lily',
        };
    },
    created() {
        // console.log('1111', testData);
        let temp1 = {};
        temp1.id = 1;
        temp1.name = testData;
        // console.log('2222', temp1);

        let temp2 = {};
        temp2.id = 2;
        temp2.name = testData;
        this.tableData.push(temp1);
        this.tableData.push(temp2);
        this.tableData.map(item => {
            console.log('1111222', item);
            item.test = this.findParentAndChildren(item.name, this.initData1);
        });
        console.log('1111333', this.tableData);
    },
    methods: {
        findParentAndChildren(data, targetName) {
            for (const group of data) {
                const target = group.children.find(person => person.label === targetName);
                if (target) {
                    const parentValue = group.value;
                    const childrenValues = target.value;
                    return [parentValue, childrenValues];
                }
            }
            return []; // 如果没有找到
        },
        parseArrayString(str) {
            console.log('1111', str);
            return JSON.parse(str || '[]');
        },
    },
};
</script>

<style scoped>
.body-content {
    width: 100%;
    height: 100%;
    display: flex;
    /* justify-content: center; */
    /* align-items: center; */
}
</style>

<!-- 一个vue element-plus的项目，el-table渲染列表数据，界面created的时候，向后端post请求数据，返回的数据是Array列表，每一项有id, content, pro_name，pro_name想用el-cascard来渲染，一共2层，第一层有4项，分别是QA,策划，前端，后端，第2层是各自职能人员的名字，pro_name在后端数据库中，是字符串类型，存着JSON.stringify后的数组字符串，该数组字符串第一项对应的是职能名称，第二项是选择的人员名字。前端收到数据后，将pro_name项进行解析，重新赋值回暂存从后端得到的数据中，el-cascader能正确识别pro_name并将解析后的值作为选中值显示出来，el-cascader还要有一个@change对应的处理函数，当选择人员变化时，将该人员的职能和名字，形成数组，以序列化数组的形式，post给后端进行数据库update -->

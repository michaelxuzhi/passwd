<template>
    <div class="body-content">
        <el-button type="primary" @click="handleExportExcel">导出</el-button>
    </div>
</template>

<script>
import * as XLSX from 'xlsx';
// import testData from '../../../staticData/testData.json';
export default {
    name: 'BodyContent',
    data() {
        return {
            tableData: [
                {
                    id: '1',
                    user_name: '小明',
                    content: '今天天气不错，心情也很好。',
                    pics: [],
                    qa_name: '小红',
                    pro_name: '小花',
                    time: '2021-08-01 10:00:00',
                    record_status: 1,
                    record_type: 'bug',
                    tag: '无',
                },
                {
                    id: '2',
                    user_name: '小红',
                    content: '今天天气不错，心情也很好。',
                    pics: [],
                    qa_name: '小明',
                    pro_name: '小花',
                    time: '2021-08-01 10:00:00',
                    record_status: 1,
                    record_type: 'bug',
                    tag: '无',
                },
                {
                    id: '3',
                    user_name: '小花',
                    content: '今天天气不错，心情也很好。',
                    pics: [],
                    qa_name: '小明',
                    pro_name: '小红',
                    time: '2021-08-01 10:00:00',
                    record_status: 1,
                    record_type: 'bug',
                    tag: '无',
                },
            ],
        };
    },
    created() {},
    methods: {
        handleExportExcel() {
            // const tableData = this.tableData;
            // 导出excel
            const ws = XLSX.utils.json_to_sheet(this.tableData);
            const wb = XLSX.utils.book_new();
            XLSX.utils.book_append_sheet(wb, ws, 'Sheet1');
            XLSX.writeFile(wb, 'test.xlsx');
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

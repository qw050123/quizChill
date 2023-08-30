<template>
    <ElTable :data="viewQuestionTableData">
        <ElTableColumn label="啟用" prop="status">
            <template #default="scope">
                <template v-if="scope.row.status">
                    <ElIcon :size="16">
                        <Select />
                    </ElIcon>
                </template>
                <templte v-else-if="!scope.row.status">
                    <ElIcon :size="16">
                        <VideoPause />
                    </ElIcon>
                </templte>
            </template>
        </ElTableColumn>
        <ElTableColumn label="題庫名稱" prop="repoName"></ElTableColumn>
        <ElTableColumn label="題目數量" prop="questionsCount"></ElTableColumn>
        <ElTableColumn label="最後更新" prop="updatedAt"></ElTableColumn>
        <ElTableColumn align="right">
            <template #header>
                <ElInput v-model="searchName" size="small" placeholder="請輸入要搜尋的名稱..."></ElInput>
            </template>
            <template #default="scope">
                <ElButton class="qc-mr-2" size="small">查看</ElButton>
                <ElButton type="danger" size="small">刪除</ElButton>
            </template>
        </ElTableColumn>
    </ElTable>
</template>
<script setup>
import { VideoPlay, VideoPause, Select } from '@element-plus/icons-vue';
let questionTableData = ref([]);
let searchName = ref('');
const viewQuestionTableData = computed(() => {
    return questionTableData.value.filter((item) => {
        if (searchName.value.length > 0) {
            if (item.repoName.includes(searchName.value)) {
                item.questionsCount = item.questions.length;
                return item;
            } else {
                return false;
            }
        } else {
            item.questionsCount = item.questions.length;
            return item;
        }
    });
});
let tempData = [
    {
        status: true,
        repoName: '123',
        questions: [1, 2, 3, 4],
        updatedAt: '2023-08-29 11:30:24',
    },
    {
        status: true,
        repoName: '124',
        questions: [1, 2, 3, 4, 5],
        updatedAt: '2023-08-29 11:30:24',
    },
    {
        status: false,
        repoName: '234',
        questions: [2, 3, 4],
        updatedAt: '2023-08-29 11:30:24',
    },
    {
        status: true,
        repoName: '12345',
        questions: [1, 2],
        updatedAt: '2023-08-29 11:30:24',
    },
];
questionTableData.value = tempData;
</script>

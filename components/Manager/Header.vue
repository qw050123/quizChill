<template>
    <div class="manager-header qc-flex qc-justify-between qc-px-10 qc-py-5">
        <div class="qc-cursor-pointer" @click="goPage('manager')">QuizChill</div>
        <ElDropdown trigger="click" placement="bottom-end">
            <ElIcon :size="22" class="qc-cursor-pointer">
                <Menu />
            </ElIcon>
            <template #dropdown>
                <ElDropdownMenu>
                    <ElDropdownItem @click="goPage('info')">個人資料</ElDropdownItem>
                    <ElDropdownItem @click="goPage('question')">我的題庫</ElDropdownItem>
                    <ElDropdownItem @click="goPage('history')">歷史資訊</ElDropdownItem>
                </ElDropdownMenu>
            </template>
        </ElDropdown>
    </div>
</template>
<script setup>
import { Menu } from '@element-plus/icons-vue';
const goPage = function (page) {
    switch (page) {
        case 'manager': {
            navigateTo(`/manager`);
            return false;
        }
        case 'info': {
            navigateTo(`/manager/info`);
            return false;
        }
        case 'question': {
            navigateTo(`/manager/question`);
            return false;
        }
        case 'history': {
            navigateTo(`/manager/history`);
            return false;
        }
        default: {
            return false;
        }
    }
};
</script>

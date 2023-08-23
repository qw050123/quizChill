<template>
    <div>
        <div class="qc-text-2xl qc-p-10">
            <div class="qc-mt-20">請輸入房間代碼</div>
            <ElInput class="qc-max-w-[300px] qc-mt-5" v-model.number="roomCode" @keyup.enter="gotoRoom">
                <template #append>
                    <el-button :icon="Search" @click="gotoRoom" />
                </template>
            </ElInput>
        </div>
    </div>
</template>
<script setup>
const roomCode = ref(null);
import { Search } from '@element-plus/icons-vue';
const gotoRoom = () => {
    navigateTo(`/member/room/${roomCode.value}`);
};
</script>

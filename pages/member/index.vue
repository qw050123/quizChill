<template>
    <div>
        <div class="qc-text-2xl qc-p-10">
            <div class="qc-mt-20">請輸入房間代碼</div>
            <ElInput class="qc-max-w-[300px] qc-mt-5" v-model.number="roomCode"></ElInput>
        </div>
    </div>
</template>
<script setup>
const roomCode = ref(null);
</script>

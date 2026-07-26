<template>
  <div class="glass-card ticker-card">
    <div class="ticker-wrapper">
      <div v-for="(item, index) in tickerItems" :key="index" class="ticker-item">
        <span>{{ item.text }}</span>
        <span style="color: var(--success-color); font-weight: bold;">[生成成功]</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const tickerItems = ref([
  { text: '用户 138****8892 成功生成了 [C1科目二倒车入库死看点点位拆解] 指南' },
  { text: '用户 159****3104 成功合成了 [C2科目三靠边停车防压线技巧] 清单' },
  { text: '用户 186****6617 成功解析了 [科目三加减档换挡不低头训练] 口诀' },
  { text: '用户 135****9023 成功生成了 [坡道定点起步防熄火防溜车] 步骤' },
  { text: '用户 173****5180 成功输出了 [考前紧张手抖呼吸调节与心理安抚] 方案' },
]);
</script>

<style scoped>
.ticker-card {
  padding: 0.6rem 1rem;
  margin-bottom: 1.25rem;
  overflow: hidden;
}

.ticker-wrapper {
  display: flex;
  gap: 2rem;
  white-space: nowrap;
  animation: ticker 25s linear infinite;
}

.ticker-wrapper:hover {
  animation-play-state: paused;
}

.ticker-item {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.85rem;
  color: var(--text-secondary);
}

@keyframes ticker {
  0% {
    transform: translateX(100%);
  }
  100% {
    transform: translateX(-100%);
  }
}
</style>

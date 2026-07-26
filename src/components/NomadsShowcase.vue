<template>
  <section class="nomads-showcase-section">
    <div class="showcase-header">
      <div class="header-left">
        <h2 class="showcase-title">驾考实战通关模板库 (Nomads Showcase)</h2>
        <p class="showcase-subtitle">精选驾考高频难点与满分看点，点击“一键套用”快速获取备考指南</p>
      </div>
      <span class="showcase-badge">已收录 {{ showcaseItems.length }} 个驾考实战模板</span>
    </div>

    <div class="showcase-grid">
      <div 
        v-for="item in showcaseItems" 
        :key="item.id" 
        class="glass-card showcase-card"
      >
        <div class="card-header">
          <span class="scenario-tag">{{ item.tag }}</span>
          <span class="usage-count">{{ item.usageCount }} 次应用</span>
        </div>

        <div class="card-content">
          <h3 class="item-title">{{ item.title }}</h3>
          <p class="item-prompt">“{{ item.prompt }}”</p>
        </div>

        <div class="card-action">
          <button class="apply-btn" @click="applyTemplate(item)">
            <span>一键套用</span>
            <svg class="arrow-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="5" y1="12" x2="19" y2="12"></line>
              <polyline points="12 5 19 12 12 19"></polyline>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

export interface ShowcaseItem {
  id: string;
  tag: string;
  title: string;
  prompt: string;
  drivingExamType?: string;
  licenseType?: string;
  drivingStage?: string;
  usageCount: string;
}

const emit = defineEmits<{
  (e: 'apply-template', payload: {
    prompt: string;
    drivingExamType?: string;
    licenseType?: string;
    drivingStage?: string;
  }): void;
}>();

const showcaseItems = computed<ShowcaseItem[]>(() => [
  {
    id: 'jiaxiao-1',
    tag: '科目二点位',
    title: '倒车入库死看点与出库打方向时机',
    prompt: '针对C1手动挡场地训练期，详细拆解倒车入库左右倒库看后视镜下沿与控制线对齐、后轮压库角打满时机及微调技巧。',
    drivingExamType: '科目二倒车入库与侧方停车口诀',
    licenseType: 'C1手动挡',
    drivingStage: '场地训练期',
    usageCount: '45.2k'
  },
  {
    id: 'jiaxiao-2',
    tag: '科目三路考',
    title: '科目三加减档换挡不低头与平稳离合配合',
    prompt: '针对C1手动挡模拟考冲刺期学员，梳理科目三加减档1挡升4挡无缝切换技巧，防换挡低头与踩空。',
    drivingExamType: '科目三路考靠边停车与变道细节',
    licenseType: 'C1手动挡',
    drivingStage: '模拟考冲刺期',
    usageCount: '38.9k'
  },
  {
    id: 'jiaxiao-3',
    tag: '坡道起步',
    title: '坡道定点停车防熄火防溜车黄金三秒',
    prompt: '针对C1手动挡场地训练期，详解坡道定点停车与起步看雨刮点位、找离合半联动半抖动状态与手刹配合。',
    drivingExamType: '科目二倒车入库与侧方停车口诀',
    licenseType: 'C1手动挡',
    drivingStage: '场地训练期',
    usageCount: '41.5k'
  },
  {
    id: 'jiaxiao-4',
    tag: '理论速记',
    title: '科一科四理论交警手势与扣分罚款口诀',
    prompt: '针对零基础刚报名前学员，梳理科目一与科目四高频错题、交警手势区别、扣12分与罚款金额记忆秘诀。',
    drivingExamType: '科目一与科目四理论错题速记',
    licenseType: 'C2自动挡',
    drivingStage: '零基础刚报名前',
    usageCount: '52.8k'
  },
  {
    id: 'jiaxiao-5',
    tag: '侧方停车',
    title: '侧方停车防压角与出库打转向灯红线警戒',
    prompt: '针对C2自动挡场地训练期，拆解侧方停车入库观察右后视镜库角出现时机、倒车打满方向及出库打左转向灯防扣分红线。',
    drivingExamType: '科目二倒车入库与侧方停车口诀',
    licenseType: 'C2自动挡',
    drivingStage: '场地训练期',
    usageCount: '36.4k'
  },
  {
    id: 'jiaxiao-6',
    tag: '心理疏导',
    title: '考前紧张手抖与面对安全员考官心态安抚',
    prompt: '针对模拟考冲刺期学员，解决考前紧张腿抖、心跳加速、听不清语音指令等问题，提供腹式呼吸法与考试心态建设。',
    drivingExamType: '驾考考前紧张心理心理安抚',
    licenseType: 'C1手动挡',
    drivingStage: '模拟考冲刺期',
    usageCount: '29.7k'
  }
]);

function applyTemplate(item: ShowcaseItem) {
  emit('apply-template', {
    prompt: item.prompt,
    drivingExamType: item.drivingExamType,
    licenseType: item.licenseType,
    drivingStage: item.drivingStage
  });
}
</script>

<style scoped>
.nomads-showcase-section {
  margin-top: 2rem;
  width: 100%;
}

.showcase-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 1.25rem;
  padding-bottom: 0.75rem;
  border-bottom: 1px solid var(--card-border);
}

.showcase-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--text-primary);
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.showcase-subtitle {
  font-size: 0.825rem;
  color: var(--text-secondary);
  margin-top: 0.25rem;
}

.showcase-badge {
  font-size: 0.75rem;
  color: #a5b4fc;
  background: rgba(99, 102, 241, 0.12);
  border: 1px solid rgba(99, 102, 241, 0.25);
  padding: 4px 10px;
  border-radius: 20px;
}

.showcase-grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 1.25rem;
}

@media (min-width: 640px) {
  .showcase-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .showcase-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

.showcase-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  padding: 1.25rem;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--card-border);
  border-radius: 14px;
  transition: all 0.25s ease;
}

.showcase-card:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(99, 102, 241, 0.4);
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.75rem;
}

.scenario-tag {
  font-size: 0.75rem;
  font-weight: 600;
  padding: 3px 8px;
  border-radius: 6px;
  background: rgba(168, 85, 247, 0.15);
  color: #c084fc;
  border: 1px solid rgba(168, 85, 247, 0.3);
}

.usage-count {
  font-size: 0.75rem;
  color: var(--text-secondary);
}

.card-content {
  margin-bottom: 1rem;
  flex: 1;
}

.item-title {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.4rem;
}

.item-prompt {
  font-size: 0.825rem;
  color: var(--text-secondary);
  line-height: 1.45;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  font-style: italic;
}

.card-action {
  padding-top: 0.75rem;
  border-top: 1px solid rgba(255, 255, 255, 0.04);
}

.apply-btn {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  padding: 0.5rem 1rem;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.3);
  border-radius: 8px;
  color: #a5b4fc;
  font-size: 0.825rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

.showcase-card:hover .apply-btn {
  background: var(--primary-gradient);
  border-color: transparent;
  color: white;
}

.arrow-icon {
  width: 14px;
  height: 14px;
  transition: transform 0.2s ease;
}

.apply-btn:hover .arrow-icon {
  transform: translateX(3px);
}
</style>

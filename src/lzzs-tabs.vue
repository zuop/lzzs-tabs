<template>
  <el-tabs v-model="activeName" class="jz-tabs" @tab-change="onTabChange()">
    <el-tab-pane
      v-for="(item, index) in list"
      :key="index"
      :name="index"
      :label="item.name"
    >
      <template #label>
        <!-- 数字超过99，则显示为99+ -->
        <el-badge
          v-if="item.count && item.count > 0"
          :value="item.count > 99 ? '99+' : item.count"
          :type="item.type"
        >
          <span>{{ item.name }}</span>
        </el-badge>
        <!-- 没有则只显示标签  -->
        <span v-else>{{ item.name }}</span>
      </template>
    </el-tab-pane>
  </el-tabs>
</template>
<script setup>
import { ref, watch } from "vue";

const activeName = ref(0);

const props = defineProps({
  modelValue: {
    type: Number,
    default: 0
  },
  list: {
    type: Array,
    default: () => []
  }
});

// 定义emit事件
const emit = defineEmits(["update:modelValue"]);

// 监听modelValue变化
watch(
  () => props.modelValue,
  (val) => {
    activeName.value = val;
  },
  { immediate: true }
);

// Tab切换事件
const onTabChange = () => {
  emit("update:modelValue", activeName.value);
};
</script>

<style lang="scss" scoped></style>

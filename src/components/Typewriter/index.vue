<script setup>
import { ref, onMounted, onUnmounted } from "vue";

// 定义 props，添加默认值
const props = defineProps({
  content: {
    type: String,
    default: "",
  },
  time: {
    type: Number,
    default: 100, // 默认时间间隔
  },
  callback: Function,
});

// 定义一个 ref 来存储当前显示的文本
const displayedText = ref("");

const intervalId = ref(null);

// 在组件挂载时开始打字机效果
onMounted(() => {
  let index = 0;

  intervalId.value = setInterval(() => {
    if (!props.content) {
      clearInterval(intervalId.value);
      return; // 检查 content 是否为空
    }

    if (index < props.content.length) {
      displayedText.value += props.content[index];
      index++;
    } else {
      clearInterval(intervalId.value);
      if (props.callback) {
        props.callback();
      }
    }
  }, props.time);

  // 在组件卸载时清除定时器
  onUnmounted(() => {
    clearInterval(intervalId.value);
  });
});
</script>

<template>
  <div>{{ displayedText }}</div>
</template>

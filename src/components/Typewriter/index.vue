<script setup>
import { ref, onMounted } from "vue";

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

// 在组件挂载时开始打字机效果
onMounted(() => {
  let index = 0;
  let lastTime = 0;

  const typeWriter = (currentTime) => {
    if (!props.content) return; // 检查 content 是否为空

    if (currentTime - lastTime >= props.time) {
      if (index < props.content.length) {
        displayedText.value += props.content[index];
        index++;
        lastTime = currentTime;
      } else {
        if (props.callback) {
          props.callback();
        }
        return; // 结束动画
      }
    }
    requestAnimationFrame(typeWriter);
  };

  requestAnimationFrame(typeWriter);
});
</script>

<template>
  <div>{{ displayedText }}</div>
</template>

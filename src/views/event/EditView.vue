<script setup lang="ts">
import { toRefs } from 'vue'
import { useRouter } from 'vue-router'
import { useEventStore } from '@/stores/event'
import { useMessageStore } from '@/stores/message'
import type { Event } from '@/type'

const router = useRouter()
const eventStore = useEventStore()
const messageStore = useMessageStore()

const props = defineProps<{
  event: Event
  id: string
}>()

const { event } = toRefs(props)

// 添加一个方法来处理编辑按钮的点击事件
const handleEditClick = () => {
  // 假设这里执行了一些更新操作
  eventStore.setEvent({ ...event.value, /* 更新后的数据 */ })

  // 设置消息
  messageStore.updateMessage('Data has been updated')

  // 设置一个定时器，在几秒钟后隐藏消息
  setTimeout(() => {
    messageStore.resetMessage()
  }, 3000) // 3秒后隐藏消息

  // 导航到详情页面
  router.push({ name: 'event-detail-view', params: { id: props.id } })
}

// 添加一个方法来处理显示消息按钮的点击事件

  // 设置一个定时器，在几秒钟后隐藏消息
  setTimeout(() => {
    messageStore.resetMessage()
  }, 3000) // 3秒后隐藏消息
</script>

<template>
  <div>
    <p>Edit event here</p>
    <button @click="handleEditClick">Save Changes</button>
  
  </div>
</template>
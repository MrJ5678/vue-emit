<!--
 * @Author: hhhhhq
 * @Date: 2021-07-02 18:18:43
 * @LastEditors: hhhhhq
 * @LastEditTime: 2021-07-03 00:07:07
 * @Description: file content
-->
<template>
  <p>Custom Text Input</p>
  <input
    type="text"
    placeholder="Custom Text Input"
    v-model="inputText"
    @change="sendChange"
  />
  <span v-if="isTyping">正在输入...</span>
</template>

<script>
import { ref, watchEffect } from "vue"
export default {
  emits: ["customChange"],
  setup(_, { emit }) {
    const inputText = ref("")
    const isTyping = ref(false)

    const sendChange = event => {
      emit("customChange", event.target.value)
    }

    watchEffect(onInvalidate => {
      if (inputText.value.length > 0) isTyping.value = true

      console.log(inputText.value)
      const showTypingStatus = setTimeout(() => {
        isTyping.value = false
      }, 2000)

      onInvalidate(() => {
        clearInterval(showTypingStatus)
      })
    })

    return {
      isTyping,
      inputText,
      sendChange,
    }
  },
  // methods: {
  //   sendChange(event) {
  //     this.$emit("customChange", event.target.value)
  //   },
  // },
}
</script>

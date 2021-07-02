<!--
 * @Author: hhhhhq
 * @Date: 2021-07-02 18:18:08
 * @LastEditors: hhhhhq
 * @LastEditTime: 2021-07-02 23:44:01
 * @Description: file content
-->
<template>
  <custom-text-input @customChange="logChange" />
</template>

<script>
import CustomTextInput from "./CustomTextInput.vue"

export default {
  components: { CustomTextInput },
  methods: {
    logChange(event) {
      console.log(event)
    },
  },
}
</script>

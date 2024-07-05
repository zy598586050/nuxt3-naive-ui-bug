<template>
  <div style="padding: 10px;display: flex;">
    <NForm ref="formRef" :model="form" :rules="rules" label-placement="left" label-width="auto" style="width: 200px;">
      <NFormItem path="email">
        <NInput v-model="form.email" placeholder="请输入邮箱" clearable />
      </NFormItem>
    </NForm>
    <NButton style="margin-left: 10px;" @click="goValdate">验证</NButton>
  </div>
</template>

<script setup lang="ts">
import { NInput, NForm, NFormItem, NButton } from 'naive-ui'

const formRef = ref()

const form = reactive({
  email: ''
})
const rules = reactive({
  email: [
    {
      required: true,
      validator: (rule: any, value: any) => {
        console.log('BUG取不到值', value)
        return true
      },
      trigger: ['input', 'blur']
    }
  ]
})

const goValdate = () => {
  formRef.value.validator((val: any) => {
    if (!val) return
  })
}
</script>

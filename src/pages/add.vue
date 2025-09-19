<script lang="ts" setup>
definePage({
  layout: 'add',
})
const info=ref({
  name:'',
  phone:'',
})
const submit=()=>{
  console.log(info.value)
  const db=uniCloud.database()
  db.collection('Contacts').add({
    name:info.value.name,
    phone:info.value.phone,
  })
}
</script>

<template>
  <view>
    <uni-easyinput
      v-model="info.name"
      type="text"
      placeholder="请输入姓名"

    />
    <uni-easyinput
      v-model="info.phone"
      type="text"
      placeholder="请输入手机号"

    />

    <button @click="submit">提交</button>

  </view>

</template>

<script lang="ts" setup>
definePage({
  layout: 'updata',
})
onLoad((options)=> {
  info.value=JSON.parse(options.info)
})

const info=ref({
  name:'',
  phone:'',
  _id:''
})
const submit=()=>{
  console.log(info.value)
  const db=uniCloud.database()
  db.collection('Contacts').doc(info.value._id).update({
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

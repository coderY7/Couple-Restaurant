<script setup lang="ts">
import { ref } from 'vue'
definePage({
  type: 'home',
})
//测试
const test =async () => {
  console.log('test')
  let data=uniCloud.importObject('uni_test')
  let result=await data.method1('test,yunduixiang111')
  console.log(result)
}
const uda = ref(null)
const longpress = (id: string) => {
  console.log(id);
  //unicloudDb.value?.remove(id)
  uda.value?.remove(id,{
      confirmTitle: '提示',
      confirmContent: '是否删除该数据',
    })
  }
const add=()=>{
  uni.navigateTo({
    url: '/pages/add',
  })
}
const updata=(item)=>{
  console.log('==',item)
  uni.navigateTo({
    url: '/pages/updata?info='+JSON.stringify(item),
  })
}
</script>

<template>
  <AppLogos />
  <InputEntry />
  <button @click="test">云对象11</button>
  <button @click="add">添加</button>
  <unicloud-db ref="uda" v-slot:default="{data, loading, error, options}" collection="Contacts">
    <view v-if="error">{{error.message}}</view>
    <view v-else>
      <uni-list>
        <uni-list-item  v-for="item in data" :to="'/pages/updata?info='+JSON.stringify(item)" :key="item._id"   :title="item.name" :note="item.phone"></uni-list-item>

      </uni-list>


    </view>
  </unicloud-db>

</template>

<style></style>

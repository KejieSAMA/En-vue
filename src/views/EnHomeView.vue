<script setup>

import HeaderTop from "@/components/HeaderTop.vue";
</script>

<template>
  <HeaderTop :param="param" />
  <div class="Item">
    重要！使用前先点击下方按钮进行数据库单词数据的导入，否则无法使用！
    <div @click="addData()">数据导入</div>
    以下为工程测试按钮
    <div>重置User表</div> 用户数据表
    <div>重置UserWord表</div> 存储用户学习进度表
    <div>重置en表</div> 存储英文单词表
    <div>重置所有表</div> 存储英文单词表
  </div>
</template>

<style scoped>
.Item {
  position: relative;
  display: flex;
  flex-direction: column;
  margin: 50px 182px;
}

.Item>div {
  width: 200px;
  border: 1px solid black;
}
</style>

<script>


import axios from 'axios'

import enData from './Data'

export default {
  data() {
    return {
      param: 'isHome'
    }
  },
  methods: {
    async addData() {
      alert("正在导入，请耐心等待!")
      const res = await axios({
        method: 'post',
        url: 'http://localhost:8000/enData/addEnDatas',
        data: enData
      })
      alert(`导入完毕，成功导入${res.data.result.count}个，导入失败${res.data.result.error}个`)
    }
  }
}
</script>
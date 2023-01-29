<template>
  <el-button type="primary" @click="add">新增</el-button>
  <el-table :data="state.tableData" style="width: 100%">
    <el-table-column fixed prop="date" label="Date" width="150" />
    <el-table-column prop="name" label="Name" width="120" />
    <el-table-column prop="state" label="State" width="120" />
    <el-table-column prop="city" label="City" width="120" />
    <el-table-column prop="address" label="Address" width="600" />
    <el-table-column prop="zip" label="Zip" width="120" />
    <el-table-column fixed="right" label="Operations" width="120">
      <template #default>
        <el-button link type="primary" size="small" @click="handleClick"
          >Detail</el-button
        >
        <el-button link type="primary" size="small">Edit</el-button>
      </template>
    </el-table-column>
  </el-table>
</template>

<script lang="ts" setup>
  import axios from 'axios';
  import { reactive } from 'vue'
  const state = reactive(
    {
        tableData: []
    }
  )
  const handleClick = () => {
    console.log('click')
  }
  axios.get('http://localhost:3004/list')
  .then(res => {
    state.tableData = res.data;
  })
  const add = () => {
    axios.post('http://localhost:3004/list', {
      id: 1,
      "date": "2016",
      "name": "Tom123",
      "state": "California123",
      "city": "Los Angeles123",
      "address": "No. 189, Grove St, Los Angeles123",
      "zip": "CA 90036123",
      "tag": "Office123"
    })
  }
</script>

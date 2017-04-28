<template>
  <div>
    <h1>Bucket List</h1>
    <el-button size="large" v-for="bucket of bucketList" :key="bucket" @click="getBucket(bucket)">{{ bucket }}</el-button>
    <br>
    <br>
    <bucket :tableData="tableData" :bucket="currentBucket"></bucket>
  </div>
</template>

<script>
import axios from 'axios'
import Bucket from '@/components/Bucket'

export default {
  mounted: async function () {
    const resp = await axios.get('http://0.0.0.0:6300/api/v1/bucket/')
    this.bucketList = resp.data
  },
  data () {
    return {
      bucketList: [],
      tableData: [],
      currentBucket: ''
    }
  },
  methods: {
    getBucket: async function (bucket) {
      this.currentBucket = bucket
      const resp = await axios.get(`http://0.0.0.0:6300/api/v1/bucket/${bucket}`)
      this.tableData = resp.data.map((v) => ({ 'key': v[0], 'val': v[1] }))
    }
  },
  components: {
    Bucket
  }
}
</script>

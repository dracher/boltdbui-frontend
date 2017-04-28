<template>
  <el-table :data="tableData" border style="width: 100%">
    <el-table-column label="Key" min-width="20%">
      <template scope="scope">
        <el-icon name="time"></el-icon>
        <span style="margin-left: 10px">{{ scope.row.key }}</span>
      </template>
    </el-table-column>
    <el-table-column label="Value" min-width="70%">
      <template scope="scope">
        {{ scope.row.val }}
      </template>
    </el-table-column>
    <el-table-column label="Operations" min-width="10%" align="center">
      <template scope="scope">
        <el-button size="small" type="success" @click="handleEdit(scope.$index, scope.row)">Edit</el-button>
        <el-button size="small" type="danger" @click="handleDelete(scope.$index, scope.row)">Delete</el-button>
      </template>
    </el-table-column>
  </el-table>
</template>


<script>
import axios from 'axios'

export default {
  mounted: async function () {
  },
  methods: {
    handleEdit (index, row) {
      console.log(index, row)
      console.log(this.bucket)
    },
    handleDelete (index, row) {
      console.log(row.key)
      axios.get(`http://0.0.0.0:6300/api/v1/d/${this.bucket}/${row.key}`)
    }
  },
  data () {
    return {
    }
  },
  props: ['tableData', 'bucket']
}
</script>

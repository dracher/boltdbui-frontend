<template>
  <div>
    <el-menu mode="horizontal" class="topnav" default-active="1">
      <el-menu-item index="1">BoltDB UI</el-menu-item>
    </el-menu>
    <br>
    <status></status>
    <br>
  </div>
</template>

<script>
import Status from '@/components/Status'

export default {
  components: {
    Status
  }
}
</script>

<style scoped>
.topnav {
  padding-left: 60px;
}
</style>

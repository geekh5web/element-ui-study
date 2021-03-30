<template>
  <div class="hello">
    <el-row>
      <el-col :span="24">
        <div class="grid-content bg-purple-dark text-center">123</div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
};
</script>

<style>
.bg-purple-dark {
  background: #99a9bf;
}
.bg-purple {
  background: #d3dce6;
}
.bg-purple-light {
  background: #e5e9f2;
}
.grid-content {
  border-radius: 4px;
  min-height: 36px;
}
.row-bg {
  padding: 10px 0;
  background-color: #f9fafc;
}
.text-center {
  text-align: center;
}
</style>

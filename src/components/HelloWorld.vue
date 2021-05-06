<template>
  <div class="hello">
    <el-row>
      <el-col :span="24">
        <div class="grid-content bg-purple-dark text-center">{{ time }}</div>
      </el-col>
    </el-row>
    <!--     <el-row>
      <el-col :span="24">
        <el-time-select
          v-model="selectTimeValue"
          :picker-options="pickerOptions"
          placeholder="请选择时间"
        ></el-time-select>
      </el-col>
    </el-row> -->
    <el-row>
      <el-col>
        <!--         <div class="block">
          <span class="demonstration">起始日期时刻为 12:00:00</span>
          <el-date-picker
            v-model="value1"
            type="datetimerange"
            start-placeholder="开始日期"
            end-placeholder="结束日期"
            :default-time="['12:00:00']"
          >
          </el-date-picker>
        </div> -->
        <div class="block">
          <span class="demonstration"
            >起始日期时刻为 12:00:00，结束日期时刻为 08:00:00</span
          >
          <el-date-picker
            v-model="value2"
            type="datetimerange"
            align="right"
            start-placeholder="开始日期"
            end-placeholder="结束日期"
            :picker-options="pickerOptionsTT"
            :default-time="['12:00:00', '08:00:00']"
          >
          </el-date-picker>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HelloWorld",
  data() {
    return {
      time: "123",
      selectTimeValue: null,
      pickerOptions: {
        start: "08:30",
        step: "00:51",
        end: "18:30",
      },
      value1: null,
      value2: null,
      pickerOptionsTT: {
        disabledDate: (time) => {
          console.log(time);
          return time.getTime() > Date.now();
        },
      },
    };
  },
  methods: {
    requestList(params) {
      var instance = axios.create({
        baseURL: "https://www.baidu.com",
      });
      var request = {
        method: "get",
        url: "/s",
        params: params,
      };
      return instance(request);
    },
    getList() {
      this.requestList({ wd: "vue" })
        .then((response) => {
          console.log(response);
        })
        .catch((erro) => {
          console.log(erro);
        });
    },
    testAxios() {
      const url = "12344";
      let data = { a: "1", b: "2" };
      axios.get(url, { params: data }).then((res) => {
        console.log(res);
      });
    },
  },
  mounted() {
    /* console.log(this.selectTimeValue);
    console.log(typeof this.selectTimeValue);
    setInterval(() => {
      console.log("定时器开始了");
      console.log(this.selectTimeValue);
      console.log(typeof this.selectTimeValue);
    }, 2000); */
    this.getList();
    this.testAxios();
  },
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
  /* text-align: center; */
  /* 不提交，直接切换分支，看看还在不在 */
}
</style>

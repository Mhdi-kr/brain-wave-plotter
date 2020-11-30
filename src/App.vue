<template>
  <el-row :gutter="20">
    <el-col :span="16">
      <el-card class="grid-content" @click="add">
        <trend
          :data="brainData"
          :gradient="['#6fa8dc', '#42b983', '#2c3e50']"
          auto-draw
          smooth
          stroke-width="0.5"
        >
        </trend>
      </el-card>
    </el-col>
    <el-col :span="8">
      <div class="grid-content bg-purple">
      </div>
    </el-col>
  </el-row>
</template>

<script>
import Trend from "vuetrend"
async function sleep(ms) {
  return new Promise(resolve => setTimeout(resolve, ms))
}
export default {
  name: "app",
  components: { 
    Trend 
  }, 
  data: () => ({
    brainData: [0, 2, 5, 9, 5, 10, 3, 5, 0, 0, 1, 8, 2, 9, 0]
  }),
  async mounted() {
    for(var i = 0; i < 2000; i++){
      this.add()
      await sleep(30)
    }
  },
  methods: {
    add(){
      this.brainData.push(Math.floor(Math.random() * 10))
      console.log(this.brainData);
    }
  }
};
</script>

<style scoped>
.el-col {
  border-radius: 4px;
}
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
</style>

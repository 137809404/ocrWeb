<template>
  <d2-container class="page">
    <div class="card-div">
      <el-row type="flex" justify="center" align="space-around">
        <el-col  :span="4" v-for="(o, index) in models" :key="index" :offset="0" >
          <div @click="tabJump('function3_test',{modelname:o.name,modelid:index})">
            <el-card :body-style="{borderRadius: '4px',height: '100%',padding: '0px' }">
              <div v-bind:style="{'width': '100%','height': '100%','background-image': 'url('+require('@/assets/image/'+o.url)+')','background-size':'cover'}">
                <div style="width: 100%;height: 40px;background-color: rgba(255,255,255,0.8);text-align: center;line-height: 40px;font-size: 20px" > {{o.name}}</div>
              </div>

            </el-card>
          </div>

        </el-col>

      </el-row>
    </div>
  </d2-container>
</template>

<script>
export default {
  name: 'page1',
  data () {
    return {
      models: [
        {
          name: '中英数字轻量',
          url: 'ocr.webp'
        },
        {
          name: '英文数字轻量',
          url: 'ocr.webp'
        },
        {
          name: '中英数字服务器',
          url: 'ocr.webp'
        },
        {
          name: '英文数字服务器',
          url: 'ocr.webp'
        }
      ]
    }
  },
  methods: {
    tabJump (path, model) {
      if (this.$route.path !== path) {
        this.$router.push({ name: path, params: model})
      }
    }
  }
}
</script>

<style scoped>
.bottom {
  float: bottom;
  margin-top: 13px;
  line-height: 12px;
}

.button {
  padding: 0;
  float: right;
}

.image {
  width: 100%;
  display: block;
}

.clearfix:before,
.clearfix:after {
  display: table;
  content: "";
}

.clearfix:after {
  clear: both
}

.el-card{
  width: 100%;
  height: 100%;
}
.el-row{
  flex-wrap: wrap;
}

.el-col{
  width: 14vw;
  height: 14vw;
  margin:20px
}
.el-col > div{
  width: 100%;
  height: 100%;
}
.actiondiv{
  height: 100%;
  width: 100%;
}
.actiondiv .el-button{
  width: 100%;
  height: 33.333%;
  margin: 0;
  border-radius: 0;
}
.add-card-content{
  height: 100%;color: #6c6c6c;font-size: 90px;display: flex;justify-content: center;align-items: center
}
.add-card-content:hover{
  height: 100%;color: #5b92ff;font-size: 90px;display: flex;justify-content: center;align-items: center
}
</style>

<template>
  <d2-container class="page">
    <div class="card-div">
      <el-row type="flex" justify="center" align="space-around">
        <el-col :span="6" :offset="0">
          <el-card :body-style="{height:'100%',padding: '0px',backgroundColor: '#efefef'}">
            <div class="add-card-content" >
              <span>
                <i class="el-icon-circle-plus"></i>
              </span>
            </div>
          </el-card>
        </el-col>
        <el-col  :span="4" v-for="(o, index) in models" :key="index" :offset="0" >
          <div @mouseenter="mouseover(index)" @mouseleave="mouseout()">
            <el-card  :body-style="{borderRadius: '4px',height: '100%',padding: '0px' }">
              <div class="actiondiv" v-show="mouseindex===index" >
                <el-button type="info">
                  修改
                </el-button>
                <el-button type="success" @click="testDialogShow=true;currentTest=index">
                  测试
                </el-button>
                <el-button type="danger">
                  删除
                </el-button>
              </div>
              <div v-show="mouseindex!==index" v-bind:style="{'width': '100%','height': '100%','background-image': 'url('+o.url+')','background-size':'cover'}">
                <div style="width: 100%;height: 50px;background-color: rgba(255,255,255,0.8);text-align: center;line-height: 50px;font-size: 20px" > {{o.name}}</div>
              </div>
<!--              <el-image-->
<!--                v-show="mouseindex!==index"-->
<!--                style="width: 100%; height: 100%;z-index: 2"-->
<!--                src="https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png"-->
<!--                fit="fill"></el-image>-->

            </el-card>
          </div>

        </el-col>

      </el-row>
    </div>
    <el-dialog
      title="模块测试"
      :visible.sync="testDialogShow"
      width="40%"
      :before-close="handleClose">
      <function1test ref="testCard" :modelid="models[currentTest]"></function1test>
    </el-dialog>
  </d2-container>
</template>

<script>
import function1test from "@/views/demo/page1/Component/function1test";
export default {
  name: 'page1',
  components: {
    function1test
  },
  data () {
    return {
      currentTest: -1,
      testDialogShow:false,
      mouseindex: -1,
      models: [
        {
          id: 0,
          name: '模板一',
          url: 'https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png'
        },
        {
          id: 1,
          name: '模板二',
          url: 'https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png'
        },
        {
          id: 2,
          name: '模板三',
          url: 'https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png'
        },
        {
          id: 3,
          name: '模板四',
          url: 'https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png'
        }
      ]
    }
  },
  methods: {
    mouseover (index) {
      this.mouseindex = index
      console.log(index)
    },
    mouseout () {
      this.mouseindex = -1
    },
    handleClose(done) {
      this.$confirm('确认关闭？')
        .then(_ => {
          this.$refs.testCard.resetImg();
          done();
        })
        .catch(_ => {});
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
  height: 100%;color:#00ced1 ;font-size: 90px;display: flex;justify-content: center;align-items: center
}
</style>

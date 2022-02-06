<template>
  <el-container>
    <el-header >
      <div style="display: flex;margin: 0 auto;justify-content: space-between">
        <div class="logo">
          <i class="el-icon-document" ></i>
          <span>工业OCR识别 beta</span>
        </div>
        <div style="display:flex;align-content: center;align-items: center">
          <el-button type="primary" v-on:click="tabJump('/login')">
            后台管理
          </el-button>
        </div>
      </div>
    </el-header>
    <div class="image">
      <el-carousel :interval="5000" trigger="click" height="800px">
        <el-carousel-item v-for="item in images" :key="item">
          <div style="color: rgba(255,255,255,0.9);display: flex;justify-content: center;align-items: center;position: absolute;top: 0;left: 0;background: rgba(0,0,0,0.7);width: 100%;height: 100%;z-index: 100">
            <div>
              <div class="mainText" style="font-size: 60px">
                Hello ! 欢 迎 访 问 本 站
              </div>
              <div class="mainText" style="font-size: 30px">
                工 业 O C R 解 决 方 案
              </div>
              <div style="width: 500px;margin: 0 auto;;text-align: center">
                <el-button round style="font-size: 20px">
                  了解更多
                  <i class="el-icon-arrow-right" ></i>
                </el-button>
              </div>

            </div>

          </div>
          <el-image
            style="width: 100%; height: 100%;position: absolute;top: 0;left: 0;"
            :src="item"
            fit="fit"
          ></el-image>

        </el-carousel-item>
      </el-carousel>
    </div>
    <div>
      sss
    </div>
    <el-main>
      <div class="info-card">
        <div class="card-title">我们拥有</div>
        <div class="card-content">
          <div class="mainText" style="color:  rgba(0,0,0,0.7);font-size: 22px">
            多种成熟OCR模型
            <br>
            识别流程自定义
            <br>
            适用于数码管、铭牌、屏幕等多种场景
            <br>
            一键生成接口，可直接部署至巡检机器人
          </div>

        </div>

      </div>
      <div class="info-card"></div>
      <div class="info-card"></div>
      <div class="info-card"></div>

    </el-main>
  </el-container>
</template>

<script>
export default {
  name: 'home',
  data () {
    return {
      images: [
        'https://bfsi.visionet.com/wp-content/uploads/2018/08/OCR-Technology-An-Old-Tool-is-New-Again.png',
        'https://www.bing.com/th?id=OHR.SalehurstChurch_ROW7578448535_1920x1080.jpg&rf=LaDigue_1920x1080.jpg'
      ]
    }
  },
  methods: {
    tabJump (path) {
      if (this.$route.path !== path) {
        this.$router.push(path)
      }
    }
  }
}
</script>

<style scoped>

.el-container{
  height: 100%;
  width: 100%;
}
.el-main{
  position: absolute;
  top: 800px;
}
.el-header{
  background-color: transparent;
  height: 70px;
  position: absolute;
  width: 100%;
  top: 0;
  left: 0;
  z-index: 900;
}
.el-header:hover{
  background-color: rgba(255, 255, 255, 0.80);
  height: 70px;
  position: absolute;
  width: 100%;
  top: 0;
  left: 0;
  z-index: 900;
}
.logo{
  color: #f5f5f5;
  font-size: 20px;
  line-height: 60px;
  font-weight: bold;
}
.el-header:hover .logo{
  color: #494949;
}
.image{
  position: absolute;
  height: 800px;
  width: 100%;
  z-index: 800;
}

.el-image{
  position: absolute;
  background: rgba(0,0,0,0.5);
}
.mainText{
  width: 100%;text-align: center;font-weight: bolder;margin: 30px 0px;
}

.info-card{
  width: 100%;
  margin: 10px 20px;
}
.card-title{
  font-size: 30px;
  font-weight: bolder;
  margin-left: 20px;
}
.el-main{
  width: 100%;
}
.card-content{
  width: 100%;
  text-align: center;
}
</style>

<template>
  <d2-container class="page">
    <div class="card-div">
      <div style="font-size: 18px"><span>⭐ <span style="font-size: 22px">{{modelname}}</span> 模型测试</span> <span style="float: right"><el-button>重新选择模型</el-button></span></div>
    </div>
    <el-divider></el-divider>
    <el-form :inline="true" :model="modelParams" class="demo-form-inline">
      <el-form-item label="模式：" style="margin-right: 30px">
        <el-button-group>
          <el-button :type="modelParams.mode===0? 'primary':''" @click="modelParams.mode=0">仅识别</el-button>
          <el-button :type="modelParams.mode===1? 'primary':''" @click="modelParams.mode=1">检测+识别</el-button>
        </el-button-group>
      </el-form-item>
      <el-form-item label="识别空格：">
        <el-switch
          v-model="modelParams.space"
          active-color="#13ce66"
          inactive-color="#cccccc">
        </el-switch>
      </el-form-item>
      <el-button type="primary" style="float: right;margin-right: 20px">识别</el-button>
    </el-form>
    <div class="imageUploadContent">
      <div class="imageUploadCard">
        <el-upload
          class="upload-demo"
          ref="upload"
          action=""
          :multiple="false"
          :http-request="handleUpload"
          :show-file-list="false"
          :on-change="handleChange"
          :on-remove="handleRemove"
          :before-upload="beforeUpload"
          :file-list="fileList"
          :auto-upload="false">
<!--          <el-button slot="trigger" size="small" type="primary">++</el-button>-->
          <el-image slot="trigger"  id="img-preview" :src="imgStream">
              <el-button slot="error">选择图片</el-button>
          </el-image>
        </el-upload>

      </div>
      <el-divider direction="vertical"></el-divider>
      <div class="imageUploadCard"></div>
    </div>

  </d2-container>
</template>

<script>
export default {
  name: 'index',
  data () {
    return {
      fileList: [],
      imgStream: '',
      modelname: '',
      modelParams: {
        mode: 0,
        space: false
      }
    }
  },
  created () {
    this.modelname = this.$route.params.modelname
  },
  methods: {
    submitUpload () {
      this.$refs.upload.submit();
    },
    setImgUrl(raw){
        this.imgStream=window.URL.createObjectURL(raw)
    },
    handleRemove (file, fileList) {
      // console.log(file, fileList);
      this.fileList=fileList;
    },
    handleChange(file,fileList){
      if (fileList.length>0) {
        this.fileList=[fileList[fileList.length-1]]
      }
      // this.fileList=fileList
      this.setImgUrl(file.raw)
    },
    // handleExceed(file,fileList){
    //   this.fileList=[file[0]]
    //   this.setImgUrl(file[0])
    // },
    beforeUpload(file){
      const isJPG = file.type === 'image/jpeg' || file.type === 'image/png';
      const isLt2M = file.size / 1024 / 1024 < 20;
      if (!isJPG) {
        this.$message.error('上传头像图片只能是 JPG 格式!');
      }
      if (!isLt2M) {
        this.$message.error('上传头像图片大小不能超过 20MB!');
      }
      return isJPG && isLt2M;
    },
    handleUpload(){

    }
  }

}
</script>

<style scoped>
.imageUploadContent{
  width: 100%;
  display: flex;
  justify-content: space-around;
  min-height: 300px;
}
.imageUploadCard{
  width: 48%;
}
/*.imageUploadCard /deep/ .el-upload--picture-card{*/
/*  width: 100%;*/
/*  height: 100%;*/
/*  line-height: 300px;*/
/*}*/
/*.imageUploadCard /deep/ div{*/
/*  width: 100%;*/
/*  height: 100%;*/
/*}*/
/*.imageUploadCard /deep/ div i{*/
/*  font-size: 40px;*/
/*}*/
.el-divider--vertical{
  height: auto;
}
#img-preview{
  width: 100%;
  height: 100%;
}
.imageUploadCard /deep/ .upload-demo{
  width: 100%;
  height: 100%;
  /*line-height: 300px;*/
}
.imageUploadCard /deep/ .el-image__error{
  width: 100%;
  height: 100%;
  /*line-height: 300px;*/
}
.imageUploadCard /deep/ .el-upload--text{
  width: 100%;
  height: 100%;
}
.el-image{
  width: 100%;
  height: 100%;
  border-radius: 15px;
  border:dashed 3px;

}
.el-image .el-button{
  width: 100%;
  height: 100%;
  border-radius: 15px;
  font-size: 20px;
}
</style>

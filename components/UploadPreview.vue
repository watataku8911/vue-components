<template>
  <div class="imgContent">
    <div class="imagePreview">
      <img :src="this.uploadedImage" width="50" height="50" alt />
    </div>
    <div class="module--spacing--largeSmall"></div>
    <label for="corporation_file" class="btn btn-success">
      画像を設定する
      <input
        type="file"
        class="file_input"
        style="display:none;"
        id="corporation_file"
        mulitple="multiple"
        @change="onDrop"
      />
    </label>
  </div>
</template>

<script>
export default {
  data() {
    return {
      uploadedImage: "",
    };
  },
  methods: {
    onDrop(event) {
      //画像データ取得
      const fileList = event.target.files;
      this.$emit("imageName", fileList[0].name);

      this.previewImage(fileList[0]);
    },

    // アップロードした画像を表示
    previewImage(file) {
      let reader = new FileReader();
      reader.onload = (e) => {
        this.uploadedImage = e.target.result;
      };
      reader.readAsDataURL(file);
    },
  },
};
</script>

<style scoped>
label {
  background-color: #fff;
  padding: 1%;
  width: 40%;
  margin: 0 auto;
  box-shadow: 1px 1px 8px 0px #000;
  display: block;
}

@media screen and (min-width: 1026px) {
  .imgContent {
    width: 90%;
    max-width: 700px;
    height: 35vh;
    margin: auto;
    margin-bottom: 10px;
    background-color: #ccc;
    padding-top: 5%;
  }

  .imagePreview {
    height: 200px;
    width: 200px;
    background: rgb(240, 240, 240);
    overflow: hidden;
    border-radius: 50%;
    background-position: center center;
    background-size: cover;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 20px;
    position: relative;
  }

  .imagePreview img {
    height: 200px;
    width: 200px;
  }
}

@media screen and (min-width: 482px) and (max-width: 1025px) {
  .imgContent {
    width: 90%;
    max-width: 700px;
    height: 20vh;
    margin: auto;
    margin-bottom: 10px;
    background-color: #ccc;
    padding-top: 5%;
  }

  .imagePreview {
    height: 100px;
    width: 100px;
    background: rgb(240, 240, 240);
    overflow: hidden;
    border-radius: 50%;
    background-position: center center;
    background-size: cover;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 20px;
    position: relative;
  }

  .imagePreview img {
    height: 100px;
    width: 100px;
  }
}

@media screen and (max-width: 481px) {
  .imgContent {
    width: 90%;
    max-width: 700px;
    height: 200px;
    margin: auto;
    margin-bottom: 10px;
    background-color: #ccc;
    padding-top: 5%;
  }

  .imagePreview {
    height: 50px;
    width: 50px;
    background: rgb(240, 240, 240);
    overflow: hidden;
    border-radius: 50%;
    background-position: center center;
    background-size: cover;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 20px;
    position: relative;
  }

  .imagePreview img {
    height: 50px;
    width: 50px;
  }
}
</style>

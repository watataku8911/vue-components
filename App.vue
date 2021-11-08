<template>
  <div class="contents">
    <!--テキストフィールド -->
    <TextInput
      v-model="text"
      type="text"
      name="text"
      placeholder="テキストボックス"
      :value="text"
    />

    <!--パスワード-->
    <TextInput
      v-model="pass"
      type="password"
      name="passwd"
      placeholder="パスワード"
      :value="pass"
    />

    <!-- テキストエリア -->
    <TextArea
      v-model="textarea"
      name="textarea"
      placeholder="テキストエリア"
      cols="76"
      rows="5"
      :value="textarea"
    />

    <!-- ラジオボタン -->
    <RadioButton v-model="checkName" :options="optionsRadio" />
    <span>選択オプション: {{ checkName }}</span>
    <div class="module--spacing--small"></div>

    <!-- セレクトボックス -->
    <SelectBox v-model="select" :options="optionsSelect" />
    <span v-if="this.select == ''">選択オプション:選択してください。</span>
    <span v-else>選択オプション: {{ select }}</span>
    <div class="module--spacing--small"></div>

    <!-- 画像アップローダー（プレビュー付き） -->
    <div class="imgContent">
      <ImagePreview :imageUrl="imageUrl" />
      <div class="module--spacing--largeSmall"></div>
      <UploadFile @fileList="setFileList" />
    </div>

    <!-- チェックボックス -->
    <CheckBox v-model="checked" :checked="checked" />
    <label>同意</label><br />

    <!-- ボタン -->
    <Button :disabled="!checked" msg="モーダルが出ます" @push="click" />
    <Modal
      title="モーダルタイトル"
      detail="モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。"
      v-if="open"
      @close="open = false"
      @modal-click="modalClick"
    />
  </div>
</template>

<script>
import TextInput from "./components/TextInput.vue";
import TextArea from "./components/TextArea.vue";
import CheckBox from "./components/CheckBox.vue";
import RadioButton from "./components/RadioButton.vue";
import SelectBox from "./components/SelectBox.vue";
import ImagePreview from "./components/ImagePreview.vue";
import UploadFile from "./components/UploadFile.vue";
import Button from "./components/Button.vue";
import Modal from "./components/Modal.vue";

export default {
  components: {
    TextInput,
    TextArea,
    CheckBox,
    RadioButton,
    SelectBox,
    ImagePreview,
    UploadFile,
    Button,
    Modal,
  },
  data() {
    return {
      text: "",
      pass: "",
      textarea: "",
      checkName: "選択してね",
      optionsRadio: [
        { label: "hoge", value: "hoge" },
        { label: "bow", value: "bow" },
        { label: "fuga", value: "fuga" },
      ],
      select: 0,
      selectValue: "",
      optionsSelect: [
        { label: "Vue.js", value: "Vue.js" },
        { label: "React", value: "React" },
        { label: "Angular", value: "Angular" },
      ],
      imageUrl: "",
      fileList: null,
      checked: false,
      open: false,
    };
  },
  methods: {
    setFileList(fileList) {
      this.fileList = fileList;
      const imageUrl = URL.createObjectURL(fileList[0]);
      this.imageUrl = imageUrl;
    },

    click() {
      this.open = true;
    },
    modalClick() {
      console.log("テキストボックスの入力内容：", this.text);
      console.log("パスワードの入力内容：", this.pass);
      console.log("テキストエリアの入力内容：", this.textarea);
      console.log("画像の名前：", this.fileList[0].name);
      alert("コンソールを見ろ！！");
      this.open = false;
      this.checked = false;

      // this.uploadImage();
    },
    uploadImage() {
      // let blob = new Blob(this.fileList, { type: "image/jpeg" });
      
      // const fileName;
      // fileName = this.genalateRandomFileName()
      
      // const uploadRef = storage.ref("images").child(fileName);
      // const uploadTask = uploadRef.put(blob);
      // uploadTask
      //   .then(() => {
      //     uploadTask.snapshot.ref.getDownloadURL().then((downloadURL) => {
      //       /* firebase strageのダウンロード先のURLが帰ってくる */
      //     });
      //   })
      //   .catch(() => {
      //     /* firebase strageに保存失敗 */
      //   });
    },

    // Generate random 16 digits strings
    genalateRandomFileName() {
      // const S =
      //   "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
      // const N = 16;
      // const fileName = Array.from(crypto.getRandomValues(new Uint32Array(N)))
      //   .map((n) => S[n % S.length])
      //   .join("");
      // return fileName;
    },
  },
};
</script>

<style>
.contents {
  width: 80%;
  margin: 0% auto;
  text-align: center;
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
}
</style>

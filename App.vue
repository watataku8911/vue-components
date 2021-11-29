<template>
  <TextInput
    v-model:modalValue="form.text"
    type="text"
    name="text"
    placeholder="テキストボックス"
    :value="form.text"
  />

  <TextInput
    v-model:modalValue="form.pass"
    type="password"
    name="passwd"
    placeholder="パスワード"
    :value="form.pass"
  />

  <TextArea
    v-model:modalValue="form.textarea"
    name="textarea"
    placeholder="テキストエリア"
    cols="86"
    rows="7"
    :value="form.textarea"
  />

  <RadioButton
    v-model:modalValue="form.checkName"
    :options="form.optionsRadio"
  />
  <div class="module--spacing--verySmall"></div>
  <span>選択オプション: {{ form.checkName }}</span>
  <div class="module--spacing--small"></div>

  <SelectBox
    v-model:select="form.select"
    name="selectbox"
    :options="form.optionsSelect"
  />
  <div class="module--spacing--verySmall"></div>
  <span v-if="form.select == ''">選択オプション:選択してください。</span>
  <span v-else>選択オプション: {{ form.select }}</span>
  <div class="module--spacing--small"></div>

  <div class="imgContent">
    <ImagePreview :imageUrl="form.imageUrl" />
    <div class="module--spacing--largeSmall"></div>
    <UploadFile @fileList="setFileList" />
  </div>

  <CheckBox v-model:change="form.checked" :checked="form.checked" />
  <label>同意</label><br />

  <Button :disabled="!form.checked" msg="モーダルが出ます" @push="handleOpen" />
  <Modal
    title="モーダルタイトル"
    detail="モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。モーダルの内容です。"
    v-if="form.open"
    @close="form.open = false"
    @modal-click="modalClick"
  />
</template>

<script>
import { reactive } from "vue";
import TextInput from "./components/TextInput.vue";
import TextArea from "./components/TextArea.vue";
import RadioButton from "./components/RadioButton.vue";
import SelectBox from "./components/SelectBox.vue";
import ImagePreview from "./components/ImagePreview.vue";
import UploadFile from "./components/UploadFile.vue";
import CheckBox from "./components/CheckBox.vue";
import Button from "./components/Button.vue";
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: {
    TextInput,
    TextArea,
    RadioButton,
    SelectBox,
    ImagePreview,
    UploadFile,
    CheckBox,
    Button,
    Modal,
  },
  setup() {
    const form = reactive({
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
    });

    const setFileList = (fileList) => {
      form.fileList = fileList;
      const imgUrl = URL.createObjectURL(fileList[0]);
      form.imageUrl = imgUrl;
    };
    const handleOpen = () => {
      form.open = true;
    };
    const modalClick = () => {
      console.log("テキストボックスの入力内容：", form.text);
      console.log("パスワードの入力内容：", form.pass);
      console.log("テキストエリアの入力内容：", form.textarea);
      console.log("画像の名前：", form.fileList[0].name);
      alert("コンソールを見ろ！！");
      form.open = false;
      form.checked = false;
      //uploadImage();
    };
    // const uploadImage = () => {
    //   let blob = new Blob(form.fileList, { type: "image/jpeg" });
    //   const fileName;
    //   fileName = genalateRandomFileName()
    //   const uploadRef = storage.ref("images").child(fileName);
    //   const uploadTask = uploadRef.put(blob);
    //   uploadTask
    //     .then(() => {
    //       uploadTask.snapshot.ref.getDownloadURL().then((downloadURL) => {
    //         /* firebase strageのダウンロード先のURLが帰ってくる */
    //       });
    //     })
    //     .catch(() => {
    //       /* firebase strageに保存失敗 */
    //     });
    // }

    // Generate random 16 digits strings
    // const genalateRandomFileName = () => {
    //   // const S =
    //   //   "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
    //   // const N = 16;
    //   // const fileName = Array.from(crypto.getRandomValues(new Uint32Array(N)))
    //   //   .map((n) => S[n % S.length])
    //   //   .join("");
    //   // return fileName;
    // }

    return {
      form,
      setFileList,
      handleOpen,
      modalClick,
    };
  },
};
</script>

<style>
#app {
  width: 1200px;
  margin: auto;
  text-align: center;
}

.module--spacing--verySmall {
  height: 10px;
}

.module--spacing--small {
  height: 20px;
}

.module--spacing--large {
  height: 30px;
}

.module--spacing--veryLarge {
  height: 40px;
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
</style>

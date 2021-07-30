<template>
  <div class="contents">
    <!--テキストフィールド -->
    <TextInput
      v-model="text"
      type="text"
      placeholder="テキストボックス"
      :value="text"
    />

    <!--パスワード-->
    <TextInput
      v-model="pass"
      type="password"
      placeholder="パスワード"
      :value="pass"
    />

    <!-- テキストエリア -->
    <TextArea
      v-model="textarea"
      placeholder="テキストエリア"
      cols="76"
      rows="5"
      :value="textarea"
    />

    <!-- チェックボックス -->
    <CheckBox v-model="checked" :checked="checked" />
    <label>同意</label><br />
    <!-- ボタン -->
    <Button :disabled="!checked" msg="ボタン" @push="click" />
  </div>
</template>

<script>
import TextInput from "./components/TextInput.vue";
import TextArea from "./components/TextArea.vue";
import CheckBox from "./components/CheckBox.vue";
import Button from "./components/Button.vue";

export default {
  components: {
    TextInput,
    TextArea,
    CheckBox,
    Button,
  },
  data() {
    return {
      text: "",
      pass: "",
      textarea: "",
      checked: false,
    };
  },
  methods: {
    click() {
      console.log("テキストボックスの入力内容：", this.text);
      console.log("パスワードの入力内容：", this.pass);
      console.log("テキストエリアの入力内容：", this.textarea);
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
</style>

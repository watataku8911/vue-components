<template>
  <div>
    <!--テキストフィールド -->
    <TextInput
      v-model="text"
      type="text"
      placeholder="テキストボックス"
      @input="inputText"
    />

    <!--パスワード-->
    <TextInput
      v-model="pass"
      type="password"
      placeholder="パスワード"
      @input="inputPass"
    />

    <!-- テキストエリア -->
    <TextArea
      v-model="textarea"
      placeholder="テキストエリア"
      cols="76"
      rows="5"
      :value="textarea"
      @input="inputArea"
    />

    <CheckBox v-model="checked" :checked="checked" />
    <p v-if="!checked">ボタンが押せません</p>
    <p v-else>ボタンが押せます</p>
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
    inputText(input) {
      this.text = input;
    },
    inputPass(input) {
      this.pass = input;
    },
    inputArea(input) {
      this.textarea = input;
    },

    click() {
      console.log("クリックしました");
      console.log(this.textarea);
      console.log(this.pass);
      console.log(this.text);
    },
  },
};
</script>

<style></style>

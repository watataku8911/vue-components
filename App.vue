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
    <SelextBox v-model="select" :options="optionsSelect" />
    <span v-if="this.select == 0">選択オプション:選択してください。</span>
    <span v-else>選択オプション: {{ select }}</span>
    <div class="module--spacing--small"></div>

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
import RadioButton from "./components/RadioButton.vue";
import SelextBox from "./components/SelectBox.vue";
import Button from "./components/Button.vue";

export default {
  components: {
    TextInput,
    TextArea,
    CheckBox,
    RadioButton,
    SelextBox,
    Button,
  },
  data() {
    return {
      text: "",
      pass: "",
      textarea: "",
      checkName: "選択してね",
      optionsRadio: [
        { label: "hoge", value: "1" },
        { label: "bow", value: "2" },
        { label: "fuga", value: "3" },
      ],
      select: 0,
      optionsSelect: [
        { label: "Vue.js", value: "1" },
        { label: "React", value: "2" },
        { label: "Angular", value: "3" },
      ],
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

.module--spacing--small {
  height: 20px;
}
</style>

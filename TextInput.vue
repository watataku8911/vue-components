<template>
	<input
			:type="this.type"
			:placeholder="this.placeholder"
			@input="updateValue"
			class="text-input"
		/>
</template>

<script>
export default {
	props: ["type", "placeholder"],
	  methods: {
    updateValue(e) {
      this.$emit("input", e.target.value);
    }
  }
}
</script>

<style  scoped>
.text-input {
	width: 100%;
	-webkit-border-radius: 3px;
	-moz-border-radius: 3px;
	border-radius: 3px;
	font-size: 3vh;
}
</style>
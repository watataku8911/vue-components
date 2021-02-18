<template>
  <input type="checkbox" @change="updateValue" />
</template>

<script>
export default {
	methods: {
		updateValue(e) {
			this.$emit("input", e.target.checked);
		}
	}
}
</script>

<style scoped>

</style>
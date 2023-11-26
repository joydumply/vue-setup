<script setup>
defineProps({
	msg: {
		type: String,
		required: true,
	},
});
</script>

<template>
	<button @click="onSendEvent">Send Event</button>
</template>

<script>
export default {
	data: () => ({
		counter: 0,
	}),
	methods: {
		onSendEvent() {
			console.log('click');
			this.counter += 1;
			this.$emit('onChangeCounter', this.counter);
		},
	},
};
</script>
<style scoped></style>

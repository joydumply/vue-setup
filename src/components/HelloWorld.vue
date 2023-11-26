<template>
	<h1>{{ title }}</h1>
	<h2>{{ test2 }}</h2>
	<div>
		{{ user }}
	</div>
	<button @click="onSendEvent">Send Event</button>
</template>

<script>
export default {
	props: {
		title: String,
		test: [String, Number], // Несколько типов для пропса указываются так
		test2: {
			// я не передал этот пропс
			type: [String, Number],
			required: true,
			default: 'Default Props Value',
		},
		user: {
			type: Object,
			// default: () => ({}),
			validator(value) {
				return value.name;
			},
		},
	},
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

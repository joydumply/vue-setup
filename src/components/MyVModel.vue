<template>
	<input
		type="text"
		v-model="textComputed"
	/>
	<h1>{{ text }}</h1>

	<input
		type="checkbox"
		v-model="checkbox"
	/>
	<h3>Checkbox value: {{ checkbox }}</h3>

	<input
		type="checkbox"
		v-model="checkboxArray"
		value="one"
	/>
	<input
		type="checkbox"
		v-model="checkboxArray"
		value="two"
	/>
	<input
		type="checkbox"
		v-model="checkboxArray"
		value="three"
	/>

	<h3>Checkbox Array: {{ checkboxArray }}</h3>

	<select v-model="select">
		<option value="audi">audi</option>
		<option value="dodge">dodge</option>
		<option value="skoda">skoda</option>
	</select>

	<h3>Select: {{ select }}</h3>
</template>

<script>
export default {
	data: () => ({
		text: '',
		checkbox: false,
		checkboxArray: [],
		select: '',
	}),
	methods: {},
	computed: {
		textComputed: {
			get() {
				return this.text;
			},
			set(value) {
				console.log('computed setter:', value);
				this.text = value;
			},
		},
	},
};
</script>

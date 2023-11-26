<template>
	<h1
		class="title"
		:class="classObj"
		:style="{ 'font-size': fontSize + 'px' }"
	>
		Hello World
	</h1>
	<HelloWorld
		:title="title"
		:test="test"
		:test2="test2"
		:user="user"
		@onChangeCounter="onChangeCounterInComponent"
	/>
	<div>
		<MyVModel />
	</div>
</template>

<script>
/**
 * * @click.prevent - click with prevent default for links
 */
import HelloWorld from './components/HelloWorld.vue';
import MyVModel from './components/MyVModel.vue';

export default {
	name: 'app',
	components: {
		HelloWorld,
		MyVModel,
	},
	data: () => ({
		title: 'Some Title',
		isActive: true,
		fontSize: 20,

		test: 'test',
		test2: 'test2',

		user: {
			name: 'Isaac',
			age: 5,
		},
		activeClass: 'my-active-class',
		secondaryClass: 'my-secondary-class',
	}),
	computed: {
		classObj() {
			return {
				'active-class': this.isActive,
				error: !this.isActive,
			};
		},
	},
	methods: {
		onChangeCounterInComponent(value) {
			console.log('In App.vue counter: ', value);
		},
	},
};
</script>

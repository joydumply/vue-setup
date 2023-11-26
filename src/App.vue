<template>
	<h1
		class="title"
		:class="classObj"
		:style="{ 'font-size': fontSize + 'px' }"
	>
		Hello World
	</h1>
	<HelloWorld @onChangeCounter="onChangeCounterInComponent" />
</template>

<script>
/**
 * * @click.prevent - click with prevent default for links
 */
import HelloWorld from './components/HelloWorld.vue';

export default {
	name: 'app',
	components: {
		HelloWorld,
	},
	data: () => ({
		isActive: true,
		fontSize: 20,

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

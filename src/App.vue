<template>
	<h1
		class="title"
		:class="classObj"
		:style="{ 'font-size': fontSize + 'px' }"
	>
		Hello World
	</h1>
</template>

<script>
/**
 * * @click.prevent - click with prevent default for links
 */

export default {
	name: 'app',
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
	methods: {},
};
</script>

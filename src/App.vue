<template>
	<h1>{{ text }}</h1>
	<input
		type="text"
		@keypress.enter="onEnterPress"
	/>
	<button @click="onClick('my value', $event)">button</button>
	<a
		href=""
		@click.prevent="onLinkClick"
	>
		Link
	</a>
</template>

<script>
/**
 * * @click.prevent - click with prevent default for links
 */

export default {
	name: 'app',
	data: () => ({
		text: '',
	}),
	methods: {
		onClick(value, event) {
			console.log(value, event);
		},
		onLinkClick() {
			console.log('link click');
		},
		onEnterPress(e) {
			this.text = e.target.value;
		},
	},
};
</script>
<style scoped>
header {
	line-height: 1.5;
}

.logo {
	display: block;
	margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
	header {
		display: flex;
		place-items: center;
		padding-right: calc(var(--section-gap) / 2);
	}

	.logo {
		margin: 0 2rem 0 0;
	}

	header .wrapper {
		display: flex;
		place-items: flex-start;
		flex-wrap: wrap;
	}
}
</style>

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
	<div>
		<ul>
			<li
				v-for="(color, index) in colors"
				:key="index"
			>
				{{ index }}
				{{ color }}
			</li>
		</ul>

		<div>
			<input
				type="text"
				@keypress.enter="addNewColor"
			/>
		</div>

		<hr />

		<ul>
			<li
				v-for="user in users"
				:key="user.id"
			>
				{{ user.name + ': ' + user.age }}
			</li>
		</ul>

		<hr />

		<ul>
			<li
				v-for="(value, name, index) in product"
				:key="index"
			>
				{{ name }}: {{ value }}
			</li>
		</ul>

		<input
			type="text"
			@keypress.enter="deleteProp"
		/>
	</div>
</template>

<script>
/**
 * * @click.prevent - click with prevent default for links
 */

export default {
	name: 'app',
	data: () => ({
		text: '',
		colors: ['orange', 'black', 'yellow', 'blue'],
		users: [
			{ name: 'Nik', age: 27, id: 991 },
			{ name: 'Anya', age: 25, id: 777 },
		],
		product: {
			brand: 'Apple',
			model: 'iPhone 12 Pro',
			price: '$1000',
		},
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
		addNewColor(e) {
			// this.colors.push(e.target.value); // в случае массивов лучше использовать функции массивов push/pop
			this.$set(this.colors, this.colors.length, e.target.value); // используется в основном для объектов чтоб отслеживать внутренние изменения
			e.target.value = '';
		},
		deleteProp(e) {
			delete this.product[e.target.value]; // работает на vue 3; не работает на vue 2
			console.log(this);
			// this.$delete(this.product, e.target.value); // используется на vue 2 и не работает на vue 3
		},
	},
};
</script>

<template>
	<h1>Hello {{ fullName }}</h1>
	<input
		type="text"
		@keypress.enter="onSetFirstName"
	/>
	<hr />
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

		first_name: 'Nik',
		last_name: 'Babichev',
	}),
	computed: {
		// fullName() {
		// 	return `${this.first_name || 'Default'} ${this.last_name || 'User'}`;
		// },

		fullName: {
			get() {
				return `${this.first_name || 'Default'} ${this.last_name || 'User'}`;
			},
			set(value) {
				console.log(value);
				const [firstName, lastName] = value.split(' ');
				this.first_name = firstName;
				this.last_name = lastName;
			},
		},
	},
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
		onSetFirstName(e) {
			// this.first_name = e.target.value;
			this.fullName = e.target.value;
		},
		onLastnameUpdate(value){
			console.log(value);
		}
	},
	watch: {
		last_name: 'onLastnameUpdate'
	}
};
</script>

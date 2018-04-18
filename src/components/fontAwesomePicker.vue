<template>
	<div id="iconPicker">
		<div class="iconPicker__header">
			<input type="text" :placeholder="searchPlaceholder" @keyup="filterIcons($event)">
		</div>
		<div class="iconPicker__body">
			<div class="iconPicker__icons">
				<a
					href="#"
					@click.stop.prevent="getIcon(icon.value, icon.name)"
					:class="`item ${selected === icon.name ? 'selected' : ''}`"
					v-for="icon in icons"
					:key="icon.value"
				>
					<i :class="'fas fa-'+icon.name"></i>
				</a>
			</div>
		</div>
	</div>
</template>

<script>
import icons from './icons';

export default {
	name: 'fontAwesomePicker',
	props: ['seachbox'],
	data () {
		return {
			selected: '',
			icons,
		};
	},
	computed: {
		searchPlaceholder () {
			return this.seachbox || 'search box';
		},
	},
	methods: {
		getIcon (icon, key) {
			this.selected = key;
			// NEED TO FIX CONVERT METHOD
			// this.convert(icon);
			this.selectIcon(icon.toUpperCase());
		},
		convert (value) {
			const newValue = value
				.charCodeAt(1)
				.toString(10)
				.replace(/\D/g, '');

			let hexValue = Number(newValue).toString(16);

			while (hexValue.length < 4) {
				hexValue = `0${hexValue}`;
			}
		},
		selectIcon (value) {
			const result = {
				className: this.selected,
				cssValue: value,
			};
			this.$emit('selectIcon', result);
		},
		filterIcons (event) {
			const search = event.target.value.trim();
			let filter = [];

			if (search.length > 3) {
				filter = icons.filter((item) => {
					const regex = new RegExp(search, 'gi');
					return item.name.match(regex);
				});
			} else if (search.length === 0) {
				this.icons = icons;
			}

			if (filter.length > 0) {
				this.icons = filter;
			}
		},
	},
};
</script>

<style>
	#iconPicker {
		position: relative;
		max-width: 292px;
		background: #f3f3f3;
	}
	.iconPicker__header {
		padding: 1em;
		border-radius: 8px 8px 0 0;
		border: 1px solid #ccc;
	}
	.iconPicker__header input {
		width: 100%;
		padding: 1em;
	}
	.iconPicker__body {
		position: relative;
		max-height: 250px;
		overflow: auto;
		padding: 1em 0 1em 1em;
		border-radius: 0 0 8px 8px;
		border: 1px solid #ccc;
	}
	.iconPicker__icons {
		display: table;
	}
	.iconPicker__icons .item {
		float: left;
	    width: 40px;
	    height: 40px;
	    padding: 12px;
	    margin: 0 12px 12px 0;
	    text-align: center;
	    border-radius: 3px;
	    font-size: 14px;
	    box-shadow: 0 0 0 1px #ddd;
	    color: inherit;
	}
	.iconPicker__icons .item.selected {
		background: #ccc;
	}
	.iconPicker__icons .item i {
		box-sizing: content-box;
	}
</style>

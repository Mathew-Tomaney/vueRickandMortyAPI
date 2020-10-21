<template lang="html">
	<li v-on:click="clickCharacter">{{ character.name }}</li>
</template>

<script>
import { eventBus } from '../main.js';

export default {
	name: 'character-select',
	props: ['character'],
	methods: {
		clickCharacter() {
			eventBus.$emit('character-selected', this.character);
		}
	}
};
</script>

<style lang="css" scoped></style>

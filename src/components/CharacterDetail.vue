<template lang="html">
	<div v-if="character">
		<p>Name: {{ character.name }}</p>
		<p>Species: {{ character.species }}</p>
		<p>Planet of Origin: {{ character.origin.name }}</p>
		<p>Number of Appearances: {{ character.episode.length }}</p>
		<img :src="character.image" alt="character-image" />
	</div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
	name: 'character-detail',
	props: ['character']
};
</script>

<style lang="css" scoped></style>

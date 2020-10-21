<template lang="html">
	<ul>
		<character-select
			v-for="(character, index) in characters"
			:character="character"
			:key="index"
		></character-select>
	</ul>
</template>

<script>
import CharacterSelect from './CharacterSelect';

export default {
	name: 'character-list',
	props: ['characters'],
	components: {
		'character-select': CharacterSelect
	}
};
</script>

<style lang="css"></style>

<template lang="html">
	<main>
		<h1>Rick and Morty Characters</h1>
		<div id="main-box">
			<character-list :characters="characters"></character-list>
			<character-detail :character="selectedCharacter"></character-detail>
		</div>
	</main>
</template>

<script>
import CharacterList from './components/CharacterList.vue';
import { eventBus } from './main';
import CharacterDetail from './components/CharacterDetail';

export default {
	name: 'app',
	data() {
		return {
			characters: [],
			selectedCharacter: null
		};
	},

	mounted() {
		fetch('https://rickandmortyapi.com/api/character/')
			.then((result) => result.json())
			.then((characters) => (this.characters = characters));

		eventBus.$on('character-selected', (character) => {
			this.selectedCharacter = character;
		});
	},

	components: {
		'character-list': CharacterList,
		'character-detail': CharacterDetail
	}
};
</script>

<style lang="css" scoped>
#main-box {
	display: flex;
	justify-content: space-between;
}

* {
	font-family: 'Red Hat Text', sans-serif;
}
</style>

// fetch api // check we have grabbed full api object // create component //
'characterList' // add functionality of characterList and import into App.vue //
create component 'characterSelect' // add functionality of selecting a single
character object // create component 'characterDetail' // add functionality to
select specific character detail (in first instance the name) // use components
to first display the character liu

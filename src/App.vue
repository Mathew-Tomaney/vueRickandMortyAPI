<template lang="html">
	<main>
		<h1>Rick and Morty Characters</h1>
    <input type="text" v-model="search">Search</input>
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
      rawCharacters: [],
			characters: [],
			selectedCharacter: null,
			search: ''
		};
	},

	mounted() {
		fetch('https://rickandmortyapi.com/api/character/')
			.then((result) => result.json())
			.then((rawCharacters) => (this.rawCharacters = rawCharacters));

		eventBus.$on('character-selected', (character) => {
			this.selectedCharacter = character;
		});
	},

	components: {
		'character-list': CharacterList,
		'character-detail': CharacterDetail
	},

	computed: {
		filteredList() {
			return this.rawCharacters.results.filter((character) => {
				return character.name
					.toLowerCase()
					.includes(this.search.toLowerCase());
			});
		}
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

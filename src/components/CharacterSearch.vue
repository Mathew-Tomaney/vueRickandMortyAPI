<template lang="html">
	<input type="text" v-model="search">

    </input>

</template>

<script>
export default {
    name: 'character-search',
    props: ['characters'],
    data: {
        search: ''
    },
    computed: {
        filteredList() {
            return this.characters.results.filter(character => {
                return character.name.toLowerCase().includes(this.search.toLowerCase())
            })
        }
    }


};
</script>

<style></style>

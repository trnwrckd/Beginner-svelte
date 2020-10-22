<script>
	import Modal from './Modal.svelte';
	import AddPerson from './AddPerson.svelte'
	let showModal = false;
	let people = [
		{name: 'tajbi', colour: 'brown', age:24, id:1},
		{name: 'afrin', colour: 'pink', age:23, id:2},
		{name: 'meem', colour: 'red', age:25, id:3}
	];
	const deletePerson= (id)=>{
		people = people.filter((person)=>person.id!=id)

	};
	const toggleModal= ()=>{
		showModal=!showModal;
	}
	const addPerson = (e)=> {
		//console.log(e.detail);
		const person = e.detail;
		people = [person, ...people];
		showModal= false;
	};
	

</script>

<Modal on:click={toggleModal} showModal={showModal}>
	<AddPerson on:addPerson={addPerson}/>
</Modal>
<main>
	<button on:click={toggleModal}> Add person</button>
	{#each people as person (person.id)}
	<div class="container border border-muted mb-2">
		<h4>{person.name}</h4>
		{#if person.name==='Fairooz Azim'}<h3> boo :*</h3>{/if}
		<p class=""style="background-color:{person.colour};">{person.age} years old, {person.colour} colour</p>
		<button on:click={()=>deletePerson(person.id)	}> delete</button>
	</div>
	{:else}
		<p class="bg-warning text-danger"> No people to show</p>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	/*  h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}*/

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
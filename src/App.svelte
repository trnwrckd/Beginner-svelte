<script>
	import Modal from './Modal.svelte';
	import AddPerson from './AddPerson.svelte'
	let showModal = false;
	let people = [
		{name: 'Person 1', colour: 'brown', skills:["Fighting"], age:24, id:1},
		{name: 'Person 2', colour: 'pink',skills:["Scrolling Facebook"], age:23, id:2},
		{name: 'Person 3', colour: 'red',skills:["Watching Tv shows","Long Drives"], age:25, id:3},
	];
	const deletePerson= (id)=>{
		people = people.filter((person)=>person.id!=id);
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
		<div class="ppl container border border-muted mb-4">
			<h4 >{person.name}</h4> <hr>
			<p style="background-color:{person.colour};">{person.age} years old</p>
			<h5 style="text-decoration:underline;"> Hobbies </h5>
			<p>
				{#each person.skills as skill}
					<li style="list-style:none;"> {skill} </li>
				{/each}
			</p>
			<button on:click={ ()=>deletePerson(person.id)	}> delete</button>
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

	.ppl{
		width: 40%;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
<script>
import {createEventDispatcher } from 'svelte';

    let dispatch = createEventDispatcher();
    let name;
    let colour;
    let age;
    let skills= [];
    

    const handleSubmit = (e)=> {
        e.preventDefault();
        const person = {
            name,
            colour,
            age,
            skills:skills,
            id: Math.random()
        };
        dispatch('addPerson', person);


    };
</script>

<form on:submit={handleSubmit}>
    <input type="text" placeholder="name" class="form-control" bind:value={name}><br>
    <input type="number" class="form-control" placeholder="age" bind:value={age}><br>
    <label for= "skl"> Hobbies:</label>
        <ul name= "skl" class="text-center">
            <input type="checkbox" class="form-check-input" bind:group={skills} value="Photography"> Photography<br>
            <input type="checkbox" class="form-check-input" bind:group={skills} value="Art"> Art<br>
            <input type="checkbox" class="form-check-input" bind:group={skills} value="Singing" >Singing<br>
            <input type="checkbox" class="form-check-input" bind:group={skills} value="Gardening" >Gardening<br>
        </ul> <br>
    <label for="col"> Colour: </label><br>
    <input type="text" class="form-control"  bind:value={colour}><br>
    <button class="btn btn-info btn-sm"> Add </button>

</form>
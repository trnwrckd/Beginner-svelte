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
            skills,
            id: Math.random()
        };
        dispatch('addPerson', person);


    };
</script>

<form on:submit={handleSubmit}>
    <input type="text" placeholder="name" bind:value={name}>
    <input type="number" placeholder="age" bind:value={age}>
    <label for= "skl"> Skills:</label>
        <ul name= "skl">
            <input type="checkbox" bind:group={skills} value="fighting"> fighting<br>
            <input type="checkbox" bind:group={skills} value="sneaking"> sneaking<br>
            <input type="checkbox" bind:group={skills} value="running" >running<br>
        </ul>
    <label for="col"> Colour: </label>
    <select bind:value={colour}>
        <option value="black">black </option>
        <option value="orange">orange </option>
        <option value="yellow">yellow</option>
        <option value="red">red </option>
    </select> <br>
    <button class="btn btn-info btn-sm"> Add </button>

</form>
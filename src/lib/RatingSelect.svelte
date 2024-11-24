<script>
    import { on } from "svelte/events";
    import { createEventDispatcher } from "svelte";
    let maxRating = 10;
    export let currentRating = maxRating;

    const dispatch = createEventDispatcher();
    const onChange = (e) => {
        //console.log(e.currentTarget.value);
        currentRating = e.currentTarget.value;
        dispatch("rating", currentRating);
    }

</script>

<ul class="rating">
    {#each Array(maxRating).fill(0).map((_, i) => i + 1) as rating}
        <li>
            <input type="radio" id="rating-{rating}" name="rating" value={rating} on:change={onChange} checked={currentRating === rating} />
            <label for="rating-{rating}">{rating}</label>
        </li>
    {/each}
</ul>

<style>
    
    .rating {
        display: flex;
        justify-content: space-evenly;
        list-style: none;
        padding: 0px;
        margin: 15px 0;
    }


    .rating li {
        position: relative;
        width: 50px;
        height: 50px;
        padding: 10px;
        text-align: center;
        border-radius: 50%;
        border: 1px solid #ff6a95;
        font-size: 19px;

    }

    .rating li:hover {
        background-color: #ff6a95;
        color: white;
    }

    .rating input {
        display: none;
    }

    .rating li label {
        cursor: pointer;
        position: absolute;
        top: 50%;
        left: 50%;
        width: 50px;
        height: 50px;
        padding: 10px;
        border-radius: 50%;
        transform: translate(-50%, -50%);
    }

    .rating input:checked + label {
        background-color: #ff6a95;
        color: white;
        font-size: 30px;
        padding: 0px;
        padding-top: 1px;
        padding-right: 1px;
    }




</style>
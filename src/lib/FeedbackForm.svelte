<script>
import {v4 as uuidv4} from 'uuid';
import Button from './Button.svelte';
import Card from './Card.svelte';
import RatingSelect from './RatingSelect.svelte';
import { FeedbackStore } from '../stores/stores';
let buttonDisabled = true;
let inputText = '';
let min = 10;
let message;
let selectedRating = 10;

const handleRating = (e) => {
    selectedRating = e.detail;
    console.log(selectedRating);
}

const handleInput = (e) => {
    inputText = e.target.value;
    if (inputText.trim().length < min) {
        buttonDisabled = true;
        message = `Input at least ${min} characters`;
    } else {
        buttonDisabled = false;
        message = null
    }
}

const handleSubmit = () => {
    if (inputText.trim().length < min) {
        message = `Input at least ${min} characters`;
        return;
    }
    let new_feedback = {
        id: uuidv4(),
        rating: +selectedRating,
        text: inputText
    }
    FeedbackStore.update((currentFeedback) => [new_feedback, ...currentFeedback]);
    console.log(new_feedback);
    inputText = '';
    selectedRating = 10;
    buttonDisabled = true;


}
</script>
<Card>
<header>
    <h2>How would you like to rate our service?</h2>
</header>
<form on:submit|preventDefault={handleSubmit}>
    <RatingSelect on:rating={handleRating} bind:currentRating={selectedRating} />
    <div class="input-group">
        <input 
        type="text" 
        placeholder="Tell us what you think" 
        bind:value={inputText}
        on:input={handleInput}/>
        <Button disabled={buttonDisabled} style="primary">Submit</Button>
    </div>
    <div class="message">
        {#if message}
        <p>{message}</p>
        {/if}
    </div>
</form>
</Card>
<style>
    header {
        margin: 0px 15px;
    }
    header h2 {
        text-align: center;
    }

    .message {
        height: 40px;
        padding: 5px 10px;
        color: red;
        font-size: 12px;
        
    }
    form {
        margin-top: 1rem;
    }

    .input-group {
        display: flex;
    }

    input {
        flex: 1;
        padding: 15px;
        border: 1px solid #ccc;
        border-radius: 15px;
        margin: 0 15px;
    }

</style>
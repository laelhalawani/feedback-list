<script>
    import Card from './Card.svelte'
    export let fb
    import { FeedbackStore } from '../stores/stores';
    
    const handleDelete = (fbId) => {
        FeedbackStore.update((currentFeedback) => currentFeedback.filter(fb => fb.id !== fbId));
    }
</script>

<Card>
    <div class="num-display">
        {fb.rating}
    </div>
    <button class="close" on:click = {() => handleDelete(fb.id)}>
        X
    </button>
    <p class="text-display">
        {fb.text}
    </p>
</Card>

<style>

    .num-display {
        position: absolute;
        top: -10px;
        left: -10px;
        font-size: 32px;
        width: 50px;
        height: 50px;
        font-weight: bold;
        background-color: palevioletred;
        padding: none; 
        border-radius: 50%;
        text-align: center;
    }

    .close {
        position: absolute;
        top: 10px;
        right: 20px;
        font-size: 1rem;
        color: red;
        cursor: pointer;
        background: none;
        border: none;
    }
    .close:hover {
        color: darkred;
    }

    .text-display {
        font-size: 1rem;
    }
</style>
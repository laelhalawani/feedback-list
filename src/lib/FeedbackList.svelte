<script>
import {fade, scale} from 'svelte/transition';
import FeedbackItem from "./FeedbackItem.svelte";
import { FeedbackStore } from '../stores/stores';

</script>

{#each $FeedbackStore as fb (fb.id)}
<div in:fade={{"duration":500}} out:scale>
    <FeedbackItem {fb} />
</div>
{/each}
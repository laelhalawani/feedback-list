<script>
    import { FeedbackStore } from "../stores/stores";
    $:count = $FeedbackStore.length;
    $:average = ($FeedbackStore.reduce((a, {rating}) => a + rating, 0) / $FeedbackStore.length).toFixed(2);

</script>

<div class="stats">
    <h4>{count} Reviews</h4>
    <h4>Ratings Average: {average}</h4>
</div>

<style>
    .stats {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin: 0px 15px;
    }
    
</style>
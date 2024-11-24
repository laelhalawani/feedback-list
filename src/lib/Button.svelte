<script>
    export let style = 'primary';
    export let disabled = false;
</script>

<button {disabled} class={style}>
    <slot></slot>
</button>

<style>
    button {
        padding: 10px 30px;
        border: 1px solid #ff6a95;
        border-radius: 0.25rem;
        cursor: pointer;
        font-size: 1rem;
        font-weight: 600;
        color: white;
        margin: 5px 10px;

    }

    button:disabled {
        cursor: not-allowed;
        background-color: #ccc;
        border: #888;
    }
    button:disabled:hover {
        background-color: #ccc;
        transform: scale(1);
    }

    .primary {
        background-color: #202142;
    }

    .secondary {
        background-color: #ff6a95;
    }

    button:hover {
        transform: scale(0.98);
        background-color: #ff6a95;
    }
</style>

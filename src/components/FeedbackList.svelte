<script>
import FeedbackItem from "./FeedbackItem.svelte";
import { fade,scale } from "svelte/transition";

    export let feedback = []
 
</script>

{#each feedback as fb (fb.id) }
<div in:scale out:fade={{duration:500}}>
<FeedbackItem item = {fb} on:delete_feedback/>
</div>
{/each}
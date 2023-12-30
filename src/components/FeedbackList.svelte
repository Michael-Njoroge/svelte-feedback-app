<script>
import { onMount,onDestroy } from "svelte";
import FeedbackItem from "./FeedbackItem.svelte";
import { fade,scale } from "svelte/transition";
import { FeedbackStore } from "../stores";

let feedback = []

const unsubscribe = FeedbackStore.subscribe((data) => feedback = data)

onMount(() => {
    console.log('mounted')
})

onDestroy(() => {
    unsubscribe
})
 
</script>

{#each feedback as fb (fb.id) }
<div in:scale out:fade={{duration:500}}>
<FeedbackItem item = {fb} on:delete_feedback/>
</div>
{/each}
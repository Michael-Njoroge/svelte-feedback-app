<script>
    import {v4 as uuidv4} from 'uuid'
    import Button from "./Button.svelte"
    import RatingSelect from "./RatingSelect.svelte";
    import Card from "./Card.svelte";
    import { createEventDispatcher } from 'svelte';

    let btnDisable = true

    let text = ''
    let rating = 10
    let min =10
    let message

    const dispatch = createEventDispatcher()

    const handleInput = () => {
        if(text.trim().length <= min){
            message = `Text must be atleast ${min} characters`
            btnDisable = true
        }else{
            message = null
            btnDisable = false
        }
    }

    const handleSelect = e => rating = e.detail

    const handleSubmit = () => {
        if(text.trim().length > min){
            const newFeedback = {
                id: uuidv4(),
                text,
                rating: +rating
            }
            dispatch('addFeedback', newFeedback)
        }

    }

</script>

<Card>
<header>
    <h2>How would you rate your service with us?</h2>
</header>

<form on:submit|preventDefault={handleSubmit}>
    <RatingSelect on:rating-select = {handleSelect}/>
    <!-- Rating Select -->
    <div class="input-group">
        <input type="text" on:input={handleInput} bind:value={text} placeholder="Tell us something that keeps you coming back">
        <Button disabled={btnDisable} type="submit">Send</Button>
    </div>
    {#if message}
    <div class="message">
        {message}
    </div>        
    {/if}

</form>
</Card>

<style>
     header {
    max-width: 400px;
    margin: auto;
  }

  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
  }

  .input-group {
    display: flex;
    flex-direction: row;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }

  input {
    flex-grow: 2;
    border: none;
    font-size: 16px;
  }

  input:focus {
    outline: none;
  }

  .message{
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  }
</style>


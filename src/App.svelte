<script>
  import FeedbackList from "./components/FeedbackList.svelte";
  import FeedbackStats from "./components/FeedbackStats.svelte";
  import FeedbackForm from "./components/FeedbackForm.svelte";
  import Button from "./components/Button.svelte"
 
 let feedback = [
  {
    id: '1',
    rating: 10,
    text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Facilis temporibus quo qui ut? Sit, alias. Nostrum, enim tempora. Aperiam harum facere iste delectus! Consequuntur alias repellendus tempore vitae nostrum esse'
  },
  {
    id: '2',
    rating: 9,
    text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Facilis temporibus quo qui ut? Sit, alias. Nostrum, enim tempora. Aperiam harum facere iste delectus! Consequuntur alias repellendus tempore vitae nostrum esse'
  },
  {
    id: '3',
    rating: 8,
    text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Facilis temporibus quo qui ut? Sit, alias. Nostrum, enim tempora. Aperiam harum facere iste delectus! Consequuntur alias repellendus tempore vitae nostrum esse'
  },
 ]

 $:count = feedback.length
 $:average = feedback.reduce((a,{rating}) => a + rating, 0) / feedback.length

 const deleteFeedback = (e) => {
  const itemId = e.detail
  feedback = feedback.filter((item) => item.id != itemId)
 }

</script>

<main class="container">
  <FeedbackForm />
  <FeedbackStats {count} {average}/>
  <FeedbackList {feedback} on:delete_feedback = {deleteFeedback}/>
</main>
 

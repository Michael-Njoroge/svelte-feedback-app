<script>
  import FeedbackList from "./components/FeedbackList.svelte";
 
 let feedback = [
  {
    id: '1',
    rating: '10',
    text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Facilis temporibus quo qui ut? Sit, alias. Nostrum, enim tempora. Aperiam harum facere iste delectus! Consequuntur alias repellendus tempore vitae nostrum esse'
  },
  {
    id: '2',
    rating: '9',
    text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Facilis temporibus quo qui ut? Sit, alias. Nostrum, enim tempora. Aperiam harum facere iste delectus! Consequuntur alias repellendus tempore vitae nostrum esse'
  },
  {
    id: '3',
    rating: '8',
    text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Facilis temporibus quo qui ut? Sit, alias. Nostrum, enim tempora. Aperiam harum facere iste delectus! Consequuntur alias repellendus tempore vitae nostrum esse'
  },
 ]

 const deleteFeedback = (e) => {
  const itemId = e.detail
  feedback = feedback.filter((item) => item.id != itemId)
 }

</script>

<main class="container">
  <FeedbackList {feedback} on:delete_feedback = {deleteFeedback}/>
</main>
 

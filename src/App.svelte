<script>
let firstname = 'Michael';
let lastName = 'Njoroge';
let color = 'blue';

const toggle = ()  => {
  color = color === 'blue' ? 'red' : 'blue'
}

$:name = firstname+ ' ' + lastName
</script>

<main>
  <h1 style="color:{color}">Hello {name}!</h1>
  <button on:click={toggle}>click</button>
</main>

<style>
  main{
    text-align: center;
    padding: 1rem;
    /* max-width: 240px; */
    margin: 0 auto;
  }
</style>

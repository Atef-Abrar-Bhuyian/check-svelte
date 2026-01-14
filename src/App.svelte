<script>
  let count = 0;

  function increment() {
    count += 1;
  }
</script>

<main>
  <h1>Welcome to Svelte!</h1>
  <p>This is a simple static page built with Svelte.</p>

  <div class="card">
    <button on:click={increment}>
      Count: {count}
    </button>
  </div>

  <p class="info">
    Click the button to see Svelte's reactivity in action.
  </p>
</main>

<style>
  main {
    text-align: center;
    padding: 2rem;
    max-width: 800px;
    margin: 0 auto;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
  }

  h1 {
    color: #ff3e00;
    font-size: 3rem;
    margin-bottom: 1rem;
  }

  p {
    font-size: 1.2rem;
    color: #333;
  }

  .card {
    margin: 2rem 0;
  }

  button {
    background-color: #ff3e00;
    color: white;
    border: none;
    padding: 1rem 2rem;
    font-size: 1.2rem;
    border-radius: 8px;
    cursor: pointer;
    transition: background-color 0.2s;
  }

  button:hover {
    background-color: #cc3200;
  }

  .info {
    color: #666;
    font-size: 1rem;
    margin-top: 1rem;
  }
</style>

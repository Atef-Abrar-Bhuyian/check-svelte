<script>
  let count = 0;
  let name = '';
  let todos = [];
  let newTodo = '';

  function increment() {
    count += 1;
  }

  function addTodo() {
    if (newTodo.trim()) {
      todos = [...todos, { id: Date.now(), text: newTodo, completed: false }];
      newTodo = '';
    }
  }

  function toggleTodo(id) {
    todos = todos.map(todo =>
      todo.id === id ? { ...todo, completed: !todo.completed } : todo
    );
  }

  function deleteTodo(id) {
    todos = todos.filter(todo => todo.id !== id);
  }
</script>

<main>
  <h1>Welcome to Svelte!</h1>
  <p>This is a simple static page built with Svelte.</p>

  <section class="greeting-section">
    <h2>Greeting</h2>
    <input
      type="text"
      bind:value={name}
      placeholder="Enter your name"
      class="text-input"
    />
    {#if name}
      <p class="greeting">Hello, {name}! 👋</p>
    {/if}
  </section>

  <section class="counter-section">
    <h2>Counter</h2>
    <div class="card">
      <button on:click={increment}>
        Count: {count}
      </button>
    </div>
    <p class="info">
      Click the button to see Svelte's reactivity in action.
    </p>
  </section>

  <section class="todo-section">
    <h2>Todo List</h2>
    <div class="todo-input">
      <input
        type="text"
        bind:value={newTodo}
        on:keypress={(e) => e.key === 'Enter' && addTodo()}
        placeholder="Add a new task"
        class="text-input"
      />
      <button on:click={addTodo} class="add-btn">Add</button>
    </div>

    {#if todos.length > 0}
      <ul class="todo-list">
        {#each todos as todo (todo.id)}
          <li class:completed={todo.completed}>
            <input
              type="checkbox"
              checked={todo.completed}
              on:change={() => toggleTodo(todo.id)}
            />
            <span>{todo.text}</span>
            <button on:click={() => deleteTodo(todo.id)} class="delete-btn">×</button>
          </li>
        {/each}
      </ul>
    {:else}
      <p class="empty-state">No tasks yet. Add one above!</p>
    {/if}
  </section>

  <footer>
    <p>Built with Svelte 💜</p>
  </footer>
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

  h2 {
    color: #333;
    font-size: 1.8rem;
    margin-bottom: 1rem;
  }

  p {
    font-size: 1.2rem;
    color: #333;
  }

  section {
    background: #f9f9f9;
    padding: 2rem;
    margin: 2rem 0;
    border-radius: 12px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  }

  .greeting-section {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
  }

  .greeting-section h2 {
    color: white;
  }

  .greeting {
    font-size: 2rem;
    margin-top: 1rem;
    font-weight: bold;
  }

  .counter-section {
    background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
  }

  .counter-section h2 {
    color: white;
  }

  .todo-section {
    background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
  }

  .todo-section h2 {
    color: white;
  }

  .text-input {
    padding: 0.8rem;
    font-size: 1rem;
    border: 2px solid rgba(255, 255, 255, 0.5);
    border-radius: 8px;
    width: 100%;
    max-width: 400px;
    background: rgba(255, 255, 255, 0.9);
    margin-bottom: 1rem;
  }

  .text-input:focus {
    outline: none;
    border-color: white;
  }

  .card {
    margin: 1rem 0;
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
    color: white;
    font-size: 1rem;
    margin-top: 1rem;
  }

  .todo-input {
    display: flex;
    gap: 1rem;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
  }

  .add-btn {
    padding: 0.8rem 2rem;
    background-color: #28a745;
  }

  .add-btn:hover {
    background-color: #218838;
  }

  .todo-list {
    list-style: none;
    padding: 0;
    margin-top: 1.5rem;
  }

  .todo-list li {
    background: white;
    padding: 1rem;
    margin: 0.5rem 0;
    border-radius: 8px;
    display: flex;
    align-items: center;
    gap: 1rem;
    text-align: left;
  }

  .todo-list li.completed span {
    text-decoration: line-through;
    color: #999;
  }

  .todo-list li input[type="checkbox"] {
    width: 20px;
    height: 20px;
    cursor: pointer;
  }

  .todo-list li span {
    flex: 1;
    font-size: 1.1rem;
  }

  .delete-btn {
    padding: 0.3rem 0.8rem;
    background-color: #dc3545;
    font-size: 1.5rem;
    line-height: 1;
  }

  .delete-btn:hover {
    background-color: #c82333;
  }

  .empty-state {
    color: rgba(255, 255, 255, 0.8);
    font-style: italic;
    margin-top: 1rem;
  }

  footer {
    margin-top: 3rem;
    padding: 1rem;
    color: #666;
  }
</style>

<script>
  // ==================== VARIABLES ====================
  // ✅ WORKING: Reactive variables (demonstrates Svelte reactivity)
  let firstNumber = 0;
  let secondNumber = 0;
  let result = 0;
  let operation = '';  // Track which operation was used

  // ==================== FUNCTIONS ====================

  // ✅ WORKING: Addition function (demonstrates basic arithmetic operation)
  function addition() {
    result = firstNumber + secondNumber;
    operation = 'Addition';
  }

  // ✅ WORKING: Multiplication function (demonstrates another operation pattern)
  function multiplication() {
    result = firstNumber * secondNumber;
    operation = 'Multiplication';
  }

  // ✅ WORKING: Clear function (demonstrates state reset pattern)
  function clear() {
    firstNumber = 0;
    secondNumber = 0;
    result = 0;
    operation = '';
  }

  // TODO 1: Implement subtraction() so result = firstNumber - secondNumber
  //   and operation = 'Subtraction'. Verify: clicking Subtract on 10 and 4
  //   shows "Subtraction Result: 6".
  function subtraction() {
  }

  // TODO 2: Implement division() with a guard. If secondNumber is 0, set
  //   result to a clear error string and label operation accordingly.
  //   Otherwise compute firstNumber / secondNumber and label 'Division'.
  //   Verify: 5 / 0 shows the error; 20 / 4 shows 5.
  function division() {
  }

  // TODO 3: Implement modulo() using the % operator and label 'Modulo'.
  //   Verify: 17 % 5 shows 2.
  function modulo() {
  }
</script>

<style>
  @import url("https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css");

  /* ✅ WORKING: Gradient background */
  :global(body) {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
    padding: 2rem 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
  }

  /* ✅ WORKING: Calculator container styling */
  .calculator-container {
    max-width: 600px;
    margin: 3rem auto;
    padding: 2.5rem;
    background: white;
    border-radius: 20px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.3);
  }

  /* ✅ WORKING: Result display styling */
  .result-display {
    font-size: 2.5rem;
    font-weight: bold;
    color: #667eea;
    margin-top: 2rem;
    padding: 1.5rem;
    background: linear-gradient(to right, #f7f9fc, #eef2f7);
    border-radius: 12px;
    text-align: center;
    min-height: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 2px solid #e0e7ff;
    transition: all 0.3s ease;
  }

  .result-display:has(.operation-label) {
    flex-direction: column;
    gap: 0.5rem;
  }

  .operation-label {
    font-size: 1rem;
    color: #64748b;
    font-weight: normal;
  }

  /* ✅ WORKING: Button enhancements */
  .btn {
    font-size: 1.1rem;
    padding: 0.8rem;
    font-weight: 600;
    border: none;
    transition: all 0.2s ease;
  }

  .btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(0,0,0,0.15);
  }

  .btn:active {
    transform: translateY(0);
  }

  /* ✅ WORKING: Input styling */
  input[type="number"] {
    font-size: 1.2rem;
    padding: 0.8rem;
    border: 2px solid #e0e7ff;
    border-radius: 8px;
    transition: border-color 0.2s;
  }

  input[type="number"]:focus {
    border-color: #667eea;
    outline: none;
    box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
  }

  /* ✅ WORKING: Clear button styling */
  .btn-danger {
    background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
    margin-top: 1rem;
  }

  h1 {
    color: #1e293b;
    font-weight: 700;
    margin-bottom: 2rem;
  }

  /* ⚠️ TODO: Add custom animation for result changes (optional)
     HINTS:
     - Use @keyframes to create a fade-in or scale animation
     - Apply animation to .result-display when result updates
     - Consider pulse or slide-in effects */
</style>

<div class="container mt-5">
  <div class="calculator-container">
    <h1 class="text-center mb-4">🧮 Math Calculator</h1>

    <!-- ✅ WORKING: Input Fields with bind:value (demonstrates two-way binding) -->
    <div class="row mb-3">
      <div class="col-md-6">
        <input
          type="number"
          class="form-control"
          placeholder="First Number"
          bind:value={firstNumber}
        />
      </div>
      <div class="col-md-6">
        <input
          type="number"
          class="form-control"
          placeholder="Second Number"
          bind:value={secondNumber}
        />
      </div>
    </div>

    <!-- ✅ WORKING: Operation Buttons (2 working, 3 for students to connect) -->
    <div class="row mb-3">
      <div class="col">
        <!-- ✅ WORKING: Addition button with on:click -->
        <button class="btn btn-primary btn-block" on:click={addition}>
          + Add
        </button>
      </div>
      <div class="col">
        <!-- TODO 4: Wire this button to subtraction(). -->
        <button class="btn btn-secondary btn-block">
          - Subtract
        </button>
      </div>
      <div class="col">
        <!-- ✅ WORKING: Multiplication button with on:click -->
        <button class="btn btn-success btn-block" on:click={multiplication}>
          × Multiply
        </button>
      </div>
      <div class="col">
        <!-- TODO 4: Wire this button to division(). -->
        <button class="btn btn-warning btn-block">
          ÷ Divide
        </button>
      </div>
      <div class="col">
        <!-- TODO 4: Wire this button to modulo(). -->
        <button class="btn btn-info btn-block">
          % Modulo
        </button>
      </div>
    </div>

    <!-- ✅ WORKING: Clear button (demonstrates state reset) -->
    <button class="btn btn-danger btn-block" on:click={clear}>
      🔄 Clear All
    </button>

    <!-- ✅ WORKING: Result Display (demonstrates reactive UI updates) -->
    <div class="result-display">
      {#if operation}
        <div>
          <div class="operation-label">{operation} Result:</div>
          <div>{result}</div>
        </div>
      {:else}
        <p style="color: #94a3b8; font-size: 1.2rem; margin: 0;">
          Enter numbers and click an operation
        </p>
      {/if}
    </div>

    <!-- ⚠️ TODO: Add calculation history feature (Extension Challenge)
         SUCCESS CRITERIA:
         - Create historyList array to store past calculations
         - Push each calculation to history when operation is performed
         - Display history list below result display
         - Include clear history button

         HINTS:
         - Use an array: let historyList = [];
         - Push format: `${firstNumber} ${operator} ${secondNumber} = ${result}`
         - Use {#each historyList as item} to display
         - Style as a list with timestamps -->
  </div>
</div>

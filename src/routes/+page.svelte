<<script>
  // ==================== VARIABLES ====================
  let firstNumber = 0;
  let secondNumber = 0;
  let result = 0;
  let operation = '';

  // ==================== FUNCTIONS ====================

  // Addition
  function addition() {
    result = firstNumber + secondNumber;
    operation = 'Addition';
  }

  // Multiplication
  function multiplication() {
    result = firstNumber * secondNumber;
    operation = 'Multiplication';
  }

  // TODO 1: Subtraction
  function subtraction() {
    result = firstNumber - secondNumber;
    operation = 'Subtraction';
  }

  // TODO 2: Division with zero guard
  function division() {
    if (secondNumber === 0) {
      result = 'Cannot divide by zero';
      operation = 'Division Error';
    } else {
      result = firstNumber / secondNumber;
      operation = 'Division';
    }
  }

  // TODO 3: Modulo
  function modulo() {
    result = firstNumber % secondNumber;
    operation = 'Modulo';
  }

  // Clear
  function clear() {
    firstNumber = 0;
    secondNumber = 0;
    result = 0;
    operation = '';
  }
</script>

<style>
  @import url("https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css");

  /* Gradient background */
  :global(body) {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
    padding: 2rem 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
  }

  /* Calculator container */
  .calculator-container {
    max-width: 600px;
    margin: 3rem auto;
    padding: 2.5rem;
    background: white;
    border-radius: 20px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.3);
  }

  /* Result display */
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

  /* Button enhancements */
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

  /* Input styling */
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

  /* Clear button styling */
  .btn-danger {
    background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
    margin-top: 1rem;
  }

  h1 {
    color: #1e293b;
    font-weight: 700;
    margin-bottom: 2rem;
  }
</style>

<div class="container mt-5">
  <div class="calculator-container">

    <h1 class="text-center mb-4">🧮 Math Calculator</h1>

    <!-- Input Fields -->
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

    <!-- Operation Buttons -->
    <div class="row mb-3">

      <!-- Addition -->
      <div class="col">
        <button
          class="btn btn-primary btn-block"
          on:click={addition}
        >
          + Add
        </button>
      </div>

      <!-- Subtraction -->
      <div class="col">
        <button
          class="btn btn-secondary btn-block"
          on:click={subtraction}
        >
          - Subtract
        </button>
      </div>

      <!-- Multiplication -->
      <div class="col">
        <button
          class="btn btn-success btn-block"
          on:click={multiplication}
        >
          × Multiply
        </button>
      </div>

      <!-- Division -->
      <div class="col">
        <button
          class="btn btn-warning btn-block"
          on:click={division}
        >
          ÷ Divide
        </button>
      </div>

      <!-- Modulo -->
      <div class="col">
        <button
          class="btn btn-info btn-block"
          on:click={modulo}
        >
          % Modulo
        </button>
      </div>

    </div>

    <!-- Clear Button -->
    <button
      class="btn btn-danger btn-block"
      on:click={clear}
    >
      🔄 Clear All
    </button>

    <!-- Result Display -->
    <div class="result-display">
      {#if operation}
        <div>
          <div class="operation-label">
            {operation} Result:
          </div>

          <div>
            {result}
          </div>
        </div>
      {:else}
        <p style="color: #94a3b8; font-size: 1.2rem; margin: 0;">
          Enter numbers and click an operation
        </p>
      {/if}
    </div>

  </div>
</div>
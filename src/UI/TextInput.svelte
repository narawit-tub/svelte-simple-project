<script>
  export let controlType;
  export let id;
  export let label;
  export let rows = null;
  export let value;
  export let valid = true;
  export let validityMessage = "";
</script>

<div class="form-control">
  <label for={id}>{label}</label>
  {#if controlType === "textarea"}
    <textarea
      class:invalid={!valid}
      row={rows}
      id="description"
      {value}
      on:input
    />
  {:else}
    <input class:invalid={!valid} type={controlType} {id} {value} on:input />
  {/if}
  {#if validityMessage && !valid}
    <p class:invalid={!valid} class="error-message">{validityMessage}</p>
  {/if}
</div>

<style>
  input,
  textarea {
    display: block;
    width: 100%;
    font: inherit;
    border: none;
    border-bottom: 2px solid #ccc;
    border-radius: 3px 3px 0 0;
    background: white;
    padding: 0.15rem 0.25rem;
    transition: border-color 0.1s ease-out;
  }

  input:focus,
  textarea:focus {
    border-color: #e40763;
    outline: none;
  }

  label {
    display: block;
    margin-bottom: 0.5rem;
    width: 100%;
  }

  .form-control {
    padding: 0.5rem 0;
    width: 100%;
    margin: 0.25rem 0;
  }

  .invalid {
    border-color: red;
    background: #fde3e3;
  }

  .error-message {
    color: red;
    margin: 0.25rem 0;
  }
</style>

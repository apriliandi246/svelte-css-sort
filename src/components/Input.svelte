<script>
   export let onSort;
   export let result;
   export let status;
   export let onClear;
   export let onCopy;
   export let properties;
   export let handleInput;
</script>

<style>
   .properties-field {
      gap: 50px;
      display: grid;
      margin: 50px 0 15px 0;
      grid-template-columns: 1fr 1fr;
      grid-template-areas: "properties result";
   }

   .input-form label {
      font-family: monospace;
      font-size: 20px;
      color: #ffffff;
   }

   .input-form textarea {
      width: 100%;
      resize: none;
      outline: none;
      padding: 15px;
      color: #f5f5f5;
      display: block;
      font-size: 18px;
      margin-top: 17px;
      white-space: pre-line;
      font-family: monospace;
      box-sizing: border-box;
      background-color: #253341;
      border: 1px solid #38444d;
      transition: background-color 0.2s;
   }

   .result textarea {
      transition: none;
      grid-area: result;
   }

   .properties textarea {
      grid-area: properties;
   }

   .input-form textarea:focus {
      background-color: #38444d;
   }

   .input-form textarea::placeholder {
      font-family: monospace;
   }

   .buttons {
      justify-content: center;
      margin: 0 auto;
      display: flex;
   }

   .buttons .btn-one,
   .buttons .btn-two,
   .buttons .btn-three {
      width: 300px;
      border: none;
      padding: 10px;
      outline: none;
      color: #ffffff;
      font-size: 20px;
      cursor: pointer;
      transition: 0.2s;
      margin-top: 45px;
      letter-spacing: 2px;
      font-family: monospace;
      box-sizing: border-box;
      background-color: #253341;
      transition: color 0.2s, background-color 0.2s;
   }

   .buttons .btn-one:hover,
   .buttons .btn-two:hover,
   .buttons .btn-three:hover {
      background-color: #192734;
      box-sizing: border-box;
      color: #87cefa;
   }

   .buttons .btn-one:disabled,
   .buttons .btn-two:disabled,
   .buttons .btn-three:disabled {
      pointer-events: none;
   }

   @media (max-width: 768px) {
      .properties-field {
         margin-bottom: 35px;
      }

      .properties-field {
         gap: 50px;
         grid-template-columns: 1fr;
         grid-template-areas: "properties" "result";
      }

      .buttons {
         align-items: center;
         flex-direction: column;
      }

      .buttons .btn-one,
      .buttons .btn-two,
      .buttons .btn-three {
         margin-top: 30px;
      }
   }
</style>

<div class="properties-field">
   <div class="input-form properties">
      <label for="properties">Properties</label>

      <textarea
         cols="65"
         rows="20"
         value={properties}
         id="properties"
         spellCheck="false"
         autoComplete="false"
         placeholder="properties...."
         on:change={handleInput} />
   </div>

   <div class="input-form result">
      <!-- svelte-ignore a11y-label-has-associated-control -->
      <label>Result</label>
      <textarea
         disabled
         cols="65"
         rows="20"
         value={result}
         placeholder="Result...." />
   </div>
</div>

<div class="buttons">
   <button
      class="btn-one"
      disabled={status.includes(true) && properties !== '' ? false : true}
      on:click={onSort}>Sort</button>

   <button
      class="btn-two"
      on:click={onCopy}
      disabled={result === '' ? true : false}>Copy</button>

   <button
      class="btn-three"
      on:click={onClear}
      disabled={result === '' ? true : false}>Clear</button>
</div>

<script>
   let properties = ``;
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

   @media (max-width: 768px) {
      .properties-field {
         margin-bottom: 35px;
      }

      .properties-field {
         gap: 50px;
         grid-template-columns: 1fr;
         grid-template-areas: "properties" "result";
      }
   }

   .buttons {
      justify-content: center;
      margin: 0 auto;
      display: flex;
   }

   .buttons .btn-one,
   .buttons .btn-two,
   .buttons .btn-three {
      transition: color 0.2s, background-color 0.2s;
      background-color: #253341;
      font-family: monospace;
      box-sizing: border-box;
      letter-spacing: 2px;
      transition: 0.2s;
      margin-top: 45px;
      font-size: 20px;
      cursor: pointer;
      color: #ffffff;
      padding: 10px;
      outline: none;
      width: 300px;
      border: none;
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
         id="properties"
         spellCheck="false"
         autoComplete="false"
         placeholder="properties...."
         bind:value={properties} />
   </div>

   <div class="input-form result">
      <!-- svelte-ignore a11y-label-has-associated-control -->
      <label>Result</label>
      <textarea disabled cols="65" rows="20" placeholder="Result...." />
   </div>
</div>

<div class="buttons">
   <button class="btn-one">Sort</button>
   <button class="btn-two"> Copy </button>
   <button class="btn-three"> Clear </button>
</div>

<script>
   export let isMin;
   export let isMax;
   export let setMenu;
</script>

<style>
   h1 {
      color: #ffffff;
      font-size: 30px;
      text-align: center;
      margin-bottom: 25px;
      font-weight: bolder;
      letter-spacing: 10px;
      font-family: monospace;
   }

   h2 {
      color: #ff4500;
      font-size: 25px;
      margin-top: 50px;
      line-height: 35px;
      text-align: center;
      font-weight: bolder;
      letter-spacing: 1px;
      font-family: monospace;
   }

   hr {
      width: 265px;
      margin-bottom: 45px;
      border: 3px dashed #f5f5f5;
   }

   @media (max-width: 552px) {
      hr {
         width: 250px;
      }
   }

   .min input[type="radio"],
   .max input[type="radio"] {
      cursor: pointer;
      height: 16px;
      width: 16px;
   }

   .min label,
   .max label {
      color: #ffffff;
      cursor: pointer;
      font-size: 23px;
      margin-left: 7px;
      font-weight: bold;
      letter-spacing: 1px;
      font-family: monospace;
   }

   .min,
   .max {
      text-align: center;
      margin-bottom: 36px;
   }
</style>

<h1>CSS-sort</h1>

<hr />

<div class="min">
   <input
      id="min"
      type="radio"
      checked={isMin}
      on:change={() => setMenu('min')} />
   <label for="min">smaller-to-bigger</label>
</div>

<div class="max">
   <input
      id="max"
      type="radio"
      checked={isMax}
      on:change={() => setMenu('max')} />
   <label for="max">bigger-to-smaller</label>
</div>

<h2>Css properties must be valid!!</h2>

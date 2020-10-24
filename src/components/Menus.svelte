<style>
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

<div class="min">
   <input type="radio" id="min" />
   <label for="min">smaller-to-bigger</label>
</div>

<div class="max">
   <input type="radio" id="max" />
   <label for="max">bigger-to-smaller</label>
</div>

<style>
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

<div class="buttons">
   <button class="btn-one">Sort</button>
   <button class="btn-two"> Copy </button>
   <button class="btn-three"> Clear </button>
</div>

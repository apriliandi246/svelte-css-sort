<script>
   import Header from "./components/Header.svelte";
   import InputField from "./components/Input.svelte";

   let isMin = false;
   let isMax = false;

   let result = "";
   let properties = "";

   function setMenu(menu) {
      if (menu === "min") {
         isMin = true;
         isMax = false;
      } else {
         isMin = false;
         isMax = true;
      }
   }

   function handleInput(e) {
      properties = e.target.value;
   }

   function onSort() {
      result = properties
         .split(";")
         .filter((property) => property.toString().trim() !== "")
         .map((property) => property.toString().trim() + ";")
         .sort((a, b) =>
            isMin == true ? a.length - b.length : b.length - a.length
         )
         .join("\n");
   }

   function onCopy() {
      navigator.clipboard.writeText(result);
      alert("Copied");
   }

   function onClear() {
      isMin = false;
      isMax = false;
      result = "";
      properties = "";
   }
</script>

<style>
   .container {
      width: 90%;
      margin: 60px auto;
   }
</style>

<div class="container">
   <Header {setMenu} {isMin} {isMax} />

   <InputField
      {result}
      {onCopy}
      {onSort}
      {onClear}
      {properties}
      {handleInput}
      status={[isMin, isMax]} />
</div>

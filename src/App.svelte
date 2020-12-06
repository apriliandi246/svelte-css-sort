<script>
   import Header from "./components/Header.svelte";
   import FormArea from "./components/FormArea.svelte";

   let result = "";
   let isMin = false;
   let isMax = false;

   function setMenu(menu) {
      if (menu === "min") {
         isMin = true;
         isMax = false;
      } else if (menu === "max") {
         isMin = false;
         isMax = true;
      } else {
         return;
      }
   }

   function sortProperties(event) {
      result = event.detail
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
   }
</script>

<style>
   .container {
      width: 90%;
      margin: 40px auto;
   }
</style>

<div class="container">
   <Header {setMenu} {isMin} {isMax} />
   <FormArea
      {result}
      {onCopy}
      {onClear}
      status={[isMin, isMax]}
      on:sortProperties={sortProperties} />
</div>

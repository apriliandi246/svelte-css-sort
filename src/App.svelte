<script>
   import Header from "./components/Header.svelte";
   import InputField from "./components/Input.svelte";

   let result = "";
   let isMin = false;
   let isMax = false;

   function setMenu(menu) {
      if (menu === "min") {
         isMin = true;
         isMax = false;
      } else {
         isMin = false;
         isMax = true;
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
      status={[isMin, isMax]}
      on:sortProperties={sortProperties} />
</div>

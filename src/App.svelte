<script>
   import { parse, generate } from "css-tree";
   import Header from "./components/Header.svelte";
   import FormArea from "./components/FormArea.svelte";

   let sortedCss = "";
   let isMin = false;
   let isMax = false;

   function setMenu(menu) {
      if (menu === "min") {
         isMin = true;
         isMax = false;
      }

      if (menu === "max") {
         isMin = false;
         isMax = true;
      }
   }

   function sortProperties(event) {
      let finalResult = "";
      const ast = parse(event.detail, { parseValue: false });
      const result = generate(ast).split("}");

      result.pop();

      for (let index = 0; index < result.length; index++) {
         const cssNode = result[index].split("{");
         const cssSelector = cssNode[0].trim();

         const cssProperties = cssNode[1]
            .trim()
            .split(";")
            .filter((property) => property.trim() !== "")
            .map((property) => property.trim() + ";")
            .sort((a, b) =>
               isMin === true ? a.length - b.length : b.length - a.length
            )
            .join("\n");

         finalResult += `${cssSelector} {\n ${cssProperties} \n}${
            index === result.length - 1 ? "\n" : "\n\n"
         }`;
      }

      sortedCss = finalResult;
   }

   function onCopy() {
      navigator.clipboard.writeText(sortedCss);
      alert("Copied");
   }

   function onClear() {
      isMin = false;
      isMax = false;
      sortedCss = "";
   }
</script>

<div class="container">
   <Header {setMenu} {isMin} {isMax} />

   <FormArea
      {onCopy}
      {onClear}
      {sortedCss}
      status={[isMin, isMax]}
      on:sortProperties={sortProperties}
   />
</div>

<style>
   .container {
      width: 90%;
      margin: 40px auto;
   }
</style>

<script>
   import Header from "./components/Header.svelte";
   import Menus from "./components/Menus.svelte";
   import InputField from "./components/InputField.svelte";
   import Buttons from "./components/Buttons.svelte";
</script>

<style>
   .container {
      width: 90%;
      margin: 40px auto;
   }
</style>

<div class="container">
   <Header />
   <Menus />
   <InputField />
   <Buttons />
</div>

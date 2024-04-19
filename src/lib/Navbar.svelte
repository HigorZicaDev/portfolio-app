<script>
  import { page } from "$app/stores";

  const items = [
    { href: "/portfolio", label: "Portefeuille" },
    { href: "/contato", label: "Contact" },
    { href: "/parcous", label: "Mon Parcous" },
  ];

  const p = $page.url;
</script>

<nav class="bg-white shadow dark:bg-gray-800">
  <div
    class="container flex items-center justify-center p-6 mx-auto text-gray-600 capitalize dark:text-gray-300"
  >
    <a href="/" class="flex items-center justify-center">
      Home
      <img class="logo mr-5" src="logo.png" alt="Logo Home" />
    </a>

    {#each items as { href, label }}
      {#if $page.url.pathname === href}
        <a
          {href}
          class="text-gray-800 transition-colors duration-300 transform dark:text-gray-200 border-b-2 hover:border-blue-500 mx-1.5 sm:mx-6"
          >{label}</a
        >
      {:else}
        <a
          {href}
          class="text-gray-800 transition-colors duration-300 transform dark:text-gray-200 border-b-2 border-transparent hover:border-blue-500 mx-1.5 sm:mx-6"
          >{label}</a
        >
      {/if}
    {/each}
  </div>
</nav>

<style>
  .logo {
    height: 2rem;
  }
</style>

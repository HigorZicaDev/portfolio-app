<script lang="ts">
  let currentCategory = "Tous";
  let currentDescription = "";
  let show = false;

  const categories = [
    "Tous",
    "Website",
    "Micro SAAS",
    "Jeux Online",
    "Backend",
  ];
  const projets = [
    {
      id: 1,
      title: "Site Web de pizzeria + menu en ligne",
      category: "Website",
      description:
        "Site institutionnel pour pizzeria avec mise en page entièrement personnalisée, système d'inscription au menu en ligne.",
      tags: ["HTML", "CSS", "JS", "PHP"],
      image: "/projetos/CardapioPizza1.png",
      link_demo: "",
      link_github: "https://github.com/HigorZicaDev/site-pizza-per-favore",
    },
    {
      id: 2,
      title: "WebSite Assistência Informática",
      category: "Website",
      description:
        "Site institutionnel conçu pour assistance technique à la diffusion. Réalisé avec Html, Css et Javascript et avec la fonction de envoyer de messages de contact via API Whatssap.",
      tags: ["HTML", "CSS", "JS"],
      image:
        "https://raw.githubusercontent.com/HigorZicaDev/site-hz-tech/main/images/Site%20HZ-TECH%201.png",
      link_demo: "https://higorzicadev.github.io/site-hz-tech",
      link_github: "https://github.com/HigorZicaDev/site-hz-tech",
    },
    {
      id: 3,
      title: "Site institutionnel + Système",
      category: "Micro SAAS",
      description:
        "Application développée pour les écoles de langues avec contrôle d'accès pour les étudiants, les enseignants et les administrateurs. Planification des cours, contrôle financier et partage du matériel d'étude.",
      tags: ["HTML", "CSS", "JS", "PHP"],
      image: "/projetos/img1-site.png",
      link_demo: "https://profmargauxfrances.com/",
      link_github: "https://github.com/HigorZicaDev/profmargaux-site",
    },
    {
      id: 4,
      title: "Application de Quizz en ligne",
      category: "Jeux Online",
      description:
        "Quizz Online est un site d'information et une société américaine de médias Internet. Fondée en 2006 à New York comme un laboratoire viral par Jonah Peretti, la société est un média mondial de divertissement présent majoritairement sur les réseaux sociaux.",
      tags: ["HTML", "CSS", "JS", "ANGULAR JS"],
      image: "/projetos/quizSiteApp1.png",
      link_demo: "https://higorzicadev.github.io/proj-quiz-frances/",
      link_github: "https://github.com/HigorZicaDev/proj-quiz-frances",
    },
    {
      id: 5,
      title: "API Consumer PHP Pure",
      category: "Backend",
      description:
        "Exemple de comment consommer une API réalisée en PHP, en utilisant CURL.",
      tags: ["PHP"],
      image: "/projetos/api-php-paises.png",
      link_demo: "",
      link_github: "https://github.com/HigorZicaDev/api_consumer_php",
    },
    {
      id: 6,
      title: "MTP - Burger Website et Menu Online",
      category: "Website",
      description:
        "Le projet est un site de type menu en ligne qui a été développé pour un restaurant de burgers dans lequel les clients peuvent commander et, après avoir finalisé leur choix, l'envoyer via l'api WhatsApp au restaurant de burger en question.",
      tags: ["HTML", "CSS", "JS"],
      image: "/projetos/mtpburger-pageHome.png",
      link_demo: "https://higorzicadev.github.io/mtp-burger/",
      link_github: "https://github.com/HigorZicaDev/mtp-burger",
    },
  ];

  function modalShow(newDescription: string) {
    show = true;
    // alert(newDescription);
    currentDescription = newDescription;
  }

  function fermerModal() {
    show = false;
  }

  function changeCategory(newCategory: string) {
    // alert(newCategory);
    currentCategory = newCategory;
    filterProjets();
  }
  export let projetsItems = projets;

  function filterProjets() {
    projetsItems = projets.filter((item) => {
      return item.category === currentCategory || currentCategory === "Tous";
    });
  }
</script>

<div class="bg-white">
  <br />
  <h1
    class="mt-4 mb-6 text-4xl text-center font-extrabold leading-none tracking-tight text-gray-900 md:text-5xl lg:text-6xl"
  >
    <span
      class="underline underline-offset-3 decoration-8 decoration-blue-400 dark:decoration-blue-600"
    >
      Mes projets personnels</span
    >
  </h1>
  <nav class="flex flex-col justify-center sm:flex-row">
    {#each categories as category}
      {#if currentCategory === category}
        <button
          class="py-4 px-6 block hover:text-blue-500 focus:outline-none text-blue-500 border-b-2 font-medium border-blue-500"
        >
          {category}
        </button>
      {:else}
        <button
          on:click={() => {
            changeCategory(category);
          }}
          class="text-gray-600 py-4 px-6 block hover:text-blue-500 focus:outline-none"
        >
          {category}
        </button>
      {/if}
    {/each}
  </nav>
</div>

<!-- Main modal -->
{#if show}
  <div
    class="relative z-10"
    aria-labelledby="modal-title"
    role="dialog"
    aria-modal="true"
    id="modalshow"
  >
    <div
      class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"
    ></div>

    <div class="fixed inset-0 z-10 w-screen overflow-y-auto">
      <div
        class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0"
      >
        <div
          class="relative transform overflow-hidden rounded-lg bg-white text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-lg"
        >
          <div class="bg-white px-4 pb-4 pt-5 sm:p-6 sm:pb-4">
            <div class="sm:flex sm:items-start">
              <div class="mt-3 text-center sm:ml-4 sm:mt-0 sm:text-left">
                <h3
                  class="text-base font-semibold leading-6 text-gray-900"
                  id="modal-title"
                >
                  Description du projet
                </h3>
                <div class="mt-2">
                  <p class="text-sm text-gray-500">
                    {currentDescription}
                  </p>
                </div>
              </div>
            </div>
          </div>
          <div class="bg-gray-50 px-4 py-3 sm:flex sm:flex-row-reverse sm:px-6">
            <button
              on:click={fermerModal}
              type="button"
              class="mt-3 inline-flex w-full justify-center rounded-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50 sm:mt-0 sm:w-auto"
              >Fermer</button
            >
          </div>
        </div>
      </div>
    </div>
  </div>
{/if}

<section class="bg-white dark:bg-gray-900">
  <div class="container px-6 py-6 mx-auto">
    <div class="grid grid-cols-1 gap-9 mt-8 xl:mt-12 xl:gap-12 lg:grid-cols-2">
      {#each projetsItems as { id, title, description, category, tags, image, link_demo, link_github }}
        <div
          class="flex items-end overflow-hidden bg-cover rounded-lg h-96"
          style="background-image:url({image})"
        >
          <div
            class="w-full px-8 py-4 overflow-hidden rounded-b-lg backdrop-blur-sm bg-white/60 dark:bg-gray-800/60"
          >
            <h2
              class="mt-4 mb-3 text-xl font-semibold text-gray-800 capitalize dark:text-white"
            >
              {title}
            </h2>
            <div class="flex flex-col">
              <div class="flex flex-row">
                {#each tags as item}
                  <span
                    class=" bg-slate-100 text-gray-800 text-xs font-bold me-2 px-2.5 py-0.5 rounded dark:bg-gray-700 dark:text-blue-400 border border-blue-100"
                    >{item}</span
                  >
                {/each}
              </div>
              <br />
              <div class="flex flex-row gap-2">
                <a
                  href={link_demo}
                  class="flex gap-3 cursor-pointer text-white font-semibold bg-gradient-to-r from-gray-800 to-black px-6 py-1 rounded-full border border-gray-600 hover:scale-105 duration-200 hover:text-gray-500 hover:border-gray-800 hover:from-black hover:to-gray-900"
                >
                  <svg
                    class="w-5 h-5"
                    stroke="currentColor"
                    stroke-width="2"
                    viewBox="0 0 24 24"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M19.5 13.5 12 21m0 0-7.5-7.5M12 21V3"
                      stroke-linejoin="round"
                      stroke-linecap="round"
                    ></path>
                  </svg>
                  Demo
                </a>
                <a
                  href={link_github}
                  class="flex gap-3 cursor-pointer text-white font-semibold bg-gradient-to-r from-gray-800 to-black px-6 py-1 rounded-full border border-gray-600 hover:scale-105 duration-200 hover:text-gray-500 hover:border-gray-800 hover:from-black hover:to-gray-900"
                >
                  <svg
                    viewBox="0 0 24 24"
                    height="24"
                    width="24"
                    xmlns="http://www.w3.org/2000/svg"
                    ><path
                      fill="#FFFFFF"
                      d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
                    ></path></svg
                  >
                  Github
                </a>
                <button
                  class="flex gap-3 cursor-pointer text-white font-semibold bg-gradient-to-r from-gray-800 to-black px-6 py-1 rounded-full border
                   border-gray-600 hover:scale-105 duration-200 hover:text-gray-500 hover:border-gray-800 hover:from-black hover:to-gray-900"
                  on:click={() => {
                    modalShow(description);
                  }}
                >
                  <img
                    width="24"
                    height="24"
                    src="https://img.icons8.com/office/30/view-file.png"
                    alt="view-file"
                  />
                  Details
                </button>
              </div>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

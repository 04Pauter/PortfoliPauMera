<script setup>
import { ref } from "vue";

const openItem = ref(null);

const toggleItem = (item) => {
  openItem.value = openItem.value === item ? null : item;
};

const skills = {
  "Quines tecnologies utilitzo?": [
    "Actualment treballo amb tecnologies com Vue, Astro*, Tailwind*, Bootstrap i altres llibreries i frameworks per al frontend, i al backend treballo amb MySQL, Java, Pascal/Delphi, Firebase, entre d’altres.",
  ],
  "La meva experiència": [
    "Tinc experiència treballant en una consultora creant ERP en Pascal mitjançant Delphi"],
  "La meva formació": [
    "Vaig estudiar una Grau Superior de Desenvolupament d'Aplicacions Multiplataforma, cosa que em va proporcionar"
    +"les bases en programacio i base de dades. Posteriorment, vaig decidir enfocar-me en el desenvolupament web i de programari." 
    +"A més, he realitzat diversos cursos per seguir formant-me com un Curs d'IA i em vaig mantenint el dia de noves tecnologies que van apareixent..",
  ],
  "Com treballo en equip?": [
    "Tinc experiència treballant en equips de multiples persones, on m’he encarregat del desenvolupament del backend. Utilitzo metodologies àgils com Scrum i Kanban, així com eines com Git, GitHub, Trello i Jira.",
  ],
  "Metodologies àgils": [
    "He treballat amb Scrum i Kanban. En Scrum vaig participar en sprints, PRs i revisions. En Kanban vaig utilitzar taulers per gestionar tasques i vaig participar en reunions diàries (dailies) per comunicar els avenços.",
  ],
};

const CategoryIcons = {
  "Quines tecnologies utilitzo?": `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="text-primary h-6 w-6 opacity-70">
      <path d="M21 3C21.5523 3 22 3.44772 22 4V20C22 20.5523 21.5523 21 21 21H3C2.44772 21 2 20.5523 2 20V4C2 3.44772 2.44772 3 3 3H21Z"/>
    </svg>`,
};
</script>

<template>
  <div class="flex flex-col items-center px-4 text-left">
    <div class="mx-auto w-full max-w-4xl">
      <h2 class="text-white text-center text-4xl font-bold drop-shadow-[2px_2px_0_#7836cf]">
        Sobre mi i la meva feina
      </h2>

      <ul class="mt-8 space-y-4 text-lg drop-shadow-[2px_2px_0_#7836cf]">
        <li v-for="(items, category) in skills" :key="category" class="w-full">
          <div
            @click="toggleItem(category)"
            class="bg-gray-900 hover:bg-opacity-80 w-full cursor-pointer overflow-hidden rounded-2xl transition-all"
          >
            <div class="flex items-center gap-3 p-4">
              

              <div class="flex grow items-center justify-between gap-2">
                <span class="text-lg text-white font-bold truncate">
                  {{ category }}
                </span>

                <!-- Fletxa -->
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 24 24"
                  fill="currentColor"
                  :class="[
                    'h-6 w-6 transform text-[#6a2cbb] transition-transform',
                    openItem === category ? 'rotate-180' : ''
                  ]"
                >
                  <path
                    d="M11.9999 13.1714L16.9497 8.22168L18.3639 9.63589L11.9999 15.9999L5.63599 9.63589L7.0502 8.22168Z"
                  />
                </svg>
              </div>
            </div>

            <!-- Contingut -->
            <div
              :class="[
                'px-4 transition-all duration-300',
                openItem === category
                  ? 'max-h-[500px] pb-4 opacity-100'
                  : 'max-h-0 opacity-0'
              ]"
            >
              <p class="text-[0.8em] text-white">
                {{ items[0] }}
              </p>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>
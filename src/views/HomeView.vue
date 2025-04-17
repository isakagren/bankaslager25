<script setup lang="ts">
import { ref, computed } from 'vue'

// --- Constants for easy modification ---
const signupOpenDateString = '2025-04-28T20:00:00' // YYYY-MM-DDTHH:MM:SS
const signupLink = '/anmalan' // Placeholder link - Update this to the actual signup page URL
// --- End Constants ---

const signupOpenDate = new Date(signupOpenDateString)
const now = ref(new Date())

// Update 'now' periodically if needed, or just check on load
setInterval(() => {
  now.value = new Date()
}, 1000) // Update every second

const isSignupOpen = computed(() => now.value >= signupOpenDate)

const formattedSignupOpenDate = computed(() => {
  return signupOpenDate
    .toLocaleString('sv-SE', {
      day: 'numeric',
      month: 'long',
      hour: '2-digit',
      minute: '2-digit',
      hour12: false, // enforce 24‑hour clock
    })
    .replace(',', '')
})
</script>

<template>
  <main class="font-sans text-black bg-white leading-relaxed">
    <!-- Banner Section -->
    <header
      class="bg-cover bg-center py-16 px-4 text-center relative text-white min-h-[300px] flex flex-col items-center justify-center"
      style="background-image: url('/images/train-bg.jpg')"
    >
      <!-- Overlay -->
      <div class="absolute inset-0 bg-black opacity-40 z-10"></div>
      <img
        src="/images/logo-large.svg"
        alt="På Spåret Logo"
        class="max-w-[90%] mb-4 relative z-20"
      />
    </header>

    <!-- Content Section Wrapper -->
    <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Signup Section -->
      <section class="my-8 p-6 bg-[#7180ac] text-white rounded-lg shadow-lg text-center">
        <div v-if="isSignupOpen">
          <h2 class="text-white mb-4 text-2xl font-bold">Anmälan är öppen!</h2>
          <p>Antalet platser är begränsat så skynda dig. Sista dag för anmälan är 21/5.</p>
          <a
            :href="signupLink"
            class="inline-block py-3 px-6 rounded-md text-lg font-bold transition duration-300 ease-in-out hover:bg-red-700 hover:text-white mt-4 no-underline"
            >Anmäl dig här</a
          >
          <p class="mt-4 opacity-80"><small>Anmälan sker endast via hemsidan.</small></p>
        </div>
        <div v-else>
          <h2 class="text-white mb-4 text-2xl font-bold">Anmälan</h2>
          <p class="text-lg font-bold py-2 px-4 rounded inline-block mb-4">
            Anmälan öppnar den {{ formattedSignupOpenDate }}
          </p>
          <p>Antalet platser är begränsat. Sista dag för anmälan är 21/5.</p>
          <p class="mt-4 opacity-80"><small>Anmälan sker endast via hemsidan.</small></p>
        </div>
      </section>

      <!-- Information Sections -->
      <section class="my-8 p-6 bg-[#EAE8FF] rounded-lg shadow-lg">
        <h2 class="text-[#456c55] border-b-2 border-[#456c55] pb-2 mb-6 text-2xl font-bold">
          Om lägret
        </h2>

        <div class="mb-8">
          <h3 class="text-[#393536] mb-2 text-xl font-semibold">Tema: Jorden runt på 4 dagar</h3>
          <p class="mb-4">
            När du checkar in på Bänkåsviken den 27 juni drar ett äventyr igång som du sent kommer
            att glömma. Vi kommer att göra en resa jorden runt, i tid och rum, med små stopp för
            bad, lägerbål, utflykter, lek, stafetter och pyssel. Vi kommer att kämpa i OS, göra en
            charterresa, gå på vandring och göra upptäckter från olika delar av världen. Vi möts
            varje morgon och eftermiddag på perrongen till storsamlingar. I den spännande teatern
            möter vi olika resenärer som hjälper oss att se på livets stora resa. Vi läser ur
            resehandboken (bibeln) och sjunger. Under hela lägret har du en reseledare som tar hand
            om dig och en mindre grupp, landslaget, med jämnåriga reskamrater.
          </p>
          <p class="italic text-[#393536] text-center mt-6 border-t border-gray-200 pt-4">
            <em>Jag är med er alla dagar – till tidens slut. <br />- Matteus 28:20</em>
          </p>
        </div>

        <div class="mb-8">
          <h3 class="text-[#393536] mb-2 text-xl font-semibold">För vem?</h3>
          <p>Lägret är för dig som nu går i klass 1-6.</p>
        </div>

        <div class="mb-8">
          <h3 class="text-[#393536] mb-2 text-xl font-semibold">Plats</h3>
          <p>Lägret hålls på Bänkåsvikens sommargård vid havet på södra Alnö utanför Sundsvall.</p>
        </div>

        <div class="mb-8">
          <h3 class="text-[#393536] mb-2 text-xl font-semibold">Boende</h3>
          <p>
            Vi bor i tält. Hör med en kompis om att dela tält. Det finns några platser i militärtält
            för dig som saknar tält eller kompis. Ange i så fall det vid anmälan. En varm sovsäck
            och liggunderlag är bra att ha.
          </p>
        </div>

        <div class="mb-8">
          <h3 class="text-[#393536] mb-2 text-xl font-semibold">Kläder och Packning</h3>
          <p>
            Tänk på att vi är ute hela lägret, så regnkläder, stövlar och varma kläder behövs.
            Packlista fås innan lägret.
          </p>
        </div>

        <div class="mb-8">
          <h3 class="text-[#393536] mb-2 text-xl font-semibold">Tider</h3>
          <p class="mb-2">
            <strong>Start:</strong> Lägret startar kl 10:30 onsdagen den 25 juni med incheckning.
          </p>
          <p>
            <strong>Avslutning:</strong> Lägret avslutas den 28 juni. 13:00 är det grillning där
            föräldrar och syskon kan köpa hamburgare, klockan 14:00 har vi en lägeravslutning då
            alla gäster bjuds på teaterföreställning och smakprov från lägret. Därefter är det dags
            för tältrivning och städning innan hemfärd.
          </p>
        </div>

        <div class="mb-8">
          <h3 class="text-[#393536] mb-2 text-xl font-semibold">Kostnad</h3>
          <p>1500 kr per deltagare.</p>
          <p>Syskon nr 2 och 3: 1000 kr per deltagare.</p>
          <p>
            Avgiften betalas så fort du fått din bekräftelse till Bänkåsvikens Framtids bankgiro
            261-5961. Ange "Barnläger" och deltagarens namn vid betalning.
          </p>
        </div>
      </section>

      <!-- Schedule Section -->
      <section class="my-8 p-6 bg-[#456c55] text-white rounded-lg shadow-lg">
        <h2 class="text-white border-b-2 border-white pb-2 mb-6 text-2xl font-bold">
          Ungefär så här kan en dag se ut
        </h2>
        <ul class="list-none p-0">
          <li class="py-2 border-b border-dashed border-white border-opacity-30">
            <strong class="inline-block w-[50px]">7.30</strong> Väckning
          </li>
          <li class="py-2 border-b border-dashed border-white border-opacity-30">
            <strong class="inline-block w-[50px]">8.00</strong> Frukost
          </li>
          <li class="py-2 border-b border-dashed border-white border-opacity-30">
            <strong class="inline-block w-[50px]">9.00</strong> Morgonsamling
          </li>
          <li class="py-2 border-b border-dashed border-white border-opacity-30">
            <strong class="inline-block w-[50px]">9.45</strong> Aktivitet 1
          </li>
          <li class="py-2 border-b border-dashed border-white border-opacity-30">
            <strong class="inline-block w-[50px]">11.15</strong> Lunch
          </li>
          <li class="py-2 border-b border-dashed border-white border-opacity-30">
            <strong class="inline-block w-[50px]">12.45</strong> Aktivitet 2
          </li>
          <li class="py-2 border-b border-dashed border-white border-opacity-30">
            <strong class="inline-block w-[50px]">14.15</strong> Mellis, fritid, bad
          </li>
          <li class="py-2 border-b border-dashed border-white border-opacity-30">
            <strong class="inline-block w-[50px]">15.30</strong> Storsamling + smågrupp
          </li>
          <li class="py-2 border-b border-dashed border-white border-opacity-30">
            <strong class="inline-block w-[50px]">17.00</strong> Middag & Kiosk
          </li>
          <li class="py-2 border-b border-dashed border-white border-opacity-30">
            Fria aktiviteter: Flaggleken, pyssel, vila…
          </li>
          <li class="py-2 border-b border-dashed border-white border-opacity-30">
            <strong class="inline-block w-[50px]">19.30</strong> Lägerbål, med bidrag från barnen.
          </li>
          <li class="py-2 border-b border-dashed border-white border-opacity-30">
            Kvällsandakt i smågruppen
          </li>
          <li class="py-2 border-b border-dashed border-white border-opacity-30">Kvällsfika</li>
          <li class="py-2 border-b border-dashed border-white border-opacity-30">
            <strong class="inline-block w-[50px]">21:15</strong> Frivillig andakt inne vid brasan
          </li>
          <li class="py-2 border-b border-dashed border-white border-opacity-30">
            <strong class="inline-block w-[50px]">21.30</strong> Läggning
          </li>
          <li class="py-2">
            <strong class="inline-block w-[50px]">22.00</strong> Tyst i lägret, tältvakt
          </li>
        </ul>
      </section>

      <!-- Other Information Section -->
      <footer class="my-8 p-6 bg-[#393536] text-white rounded-lg shadow-lg text-center">
        <h2 class="text-white border-b-2 border-white pb-2 mb-6 text-2xl font-bold">
          Övrig Information
        </h2>
        <div class="mb-8">
          <h3 class="text-[#7180ac] mb-2 text-xl font-semibold">Arrangörer</h3>
          <p>
            Lägret arrangeras av Föreningen Bänkåsvikens Framtid i samarbete med Studieförbundet
            Bilda och församlingar i området.
          </p>
          <img
            src="/images/bilda-logo.svg"
            alt="Studieförbundet Bilda Logotyp"
            class="max-w-[150px] mt-4 mx-auto p-1 rounded"
          />
        </div>
        <div class="mb-8">
          <h3 class="text-[#7180ac] mb-2 text-xl font-semibold">Hjälpa till?</h3>
          <p>
            Föräldrar och ledare: Hör av dig om du vill vara med som ledare, eller kan hjälpa till
            praktiskt under lägret, med mat, disk, städning, handling. Du behövs för att göra lägret
            möjligt!
          </p>
        </div>
        <div class="mb-8">
          <h3 class="text-[#7180ac] mb-2 text-xl font-semibold">Frågor och information</h3>
          <p>
            Kontakta oss via e-post:
            <a href="mailto:barnlager@baptistsundsvall.se" class="text-[#7180ac] hover:underline"
              >barnlager@baptistsundsvall.se</a
            >
          </p>
          <p>Eller ring:</p>
          <ul class="list-none p-0">
            <li class="mb-2">
              Elisabeth Ågren:
              <a href="tel:0706518214" class="text-[#7180ac] hover:underline">070-651 82 14</a>
            </li>
            <li>
              Elsa Cronhjort:
              <a href="tel:0762092902" class="text-[#7180ac] hover:underline">076-209 29 02</a>
            </li>
          </ul>
        </div>
        <img
          src="/images/break.png"
          alt="Dekorativ bild"
          class="max-w-[200px] w-full mx-auto mt-8 opacity-70"
        />
      </footer>
    </div>
    <!-- End Content Section Wrapper -->
  </main>
</template>

<!-- Removed scoped style block -->

<template>
    <div class="flex items-center justify-center">
   
      <div v-if="!isVerified" class="bg-white shadow-md rounded-lg p-6 w-full max-w-2xl">
        <!-- Verification Info -->
        <div class="flex flex-col items-center mb-6">
          <div class="w-12 h-12 p-2 bg-green-100 rounded-full flex items-center justify-center mb-3">
            <svg width="41" height="40" viewBox="0 0 41 40" fill="none">
  <path d="M20.5 18C23.8137 18 26.5 15.3137 26.5 12C26.5 8.68629 23.8137 6 20.5 6C17.1863 6 14.5 8.68629 14.5 12C14.5 15.3137 17.1863 18 20.5 18Z" fill="#219653"/>
  <path d="M6.5 36C6.5 28.268 12.768 22 20.5 22C28.232 22 34.5 28.268 34.5 36H6.5Z" fill="#219653"/>
</svg>
          </div>
          <h1 class="text-xl font-medium text-gray-800 mb-1">Identity Verification</h1>
          <p class="text-sm text-gray-500">Help us verify your identity</p>
        </div>
  
        <div>
          <div class="mb-4">
            <h2 class="text-lg font-medium text-blue-600">1. Degoren Kall</h2>
            <ul class="text-sm text-gray-700 space-y-2 mt-2 list-disc list-inside ml-2">
              <li>Lorem ipsum kall gigarade heminade. Sopoment decingen ran ånissa klimatlarm.</li>
              <li>Bloppis teranade pregt, fan att dessa. Beköll reng digon orodett.</li>
              <li>Degören låpeledes, atrest. Söfase pararen för blockkedja om henade.</li>
              <li>Päskap pesade. Kront lun även om sogt losaras om monolusam.</li>
            </ul>
          </div>
  
          <div class="mb-6">
            <h2 class="text-lg font-medium text-blue-600">2. Bloppis teranade</h2>
            <ul class="text-sm text-gray-700 space-y-2 mt-2 list-disc list-inside ml-2">
              <li>Lorem ipsum kall gigarade heminade. Sopoment decingen ran ånissa klimatlarm.</li>
              <li>Bloppis teranade pregt, fan att dessa. Beköll reng digon orodett.</li>
              <li>Degören låpeledes, atrest. Söfase pararen för blockkedja om henade.</li>
              <li>Päskap pesade. Kront lun även om sogt losaras om monolusam.</li>
            </ul>
          </div>
  
          <button
            @click="verifyIdentity"
            class="py-2 px-4 bg-blue-600 text-white text-sm font-medium rounded-md hover:bg-blue-500 focus:outline-none focus:ring focus:ring-blue-300"
          >
            Start Verification
          </button>
        </div>
      </div>
  
      <!-- Verified Section -->
      <div v-else class="bg-white shadow-md rounded-lg p-8 w-full max-w-2xl text-center">
        <div class="flex justify-center mb-6">
          <div class="relative">
            <div class="rounded-lg p-4 flex items-center justify-center">
                <svg width="121" height="85" viewBox="0 0 121 85" fill="none">
  <path d="M101.458 84.8046H5.33988C2.39085 84.8046 0 82.4138 0 79.4648V20.7267C0 17.7777 2.39085 15.3868 5.33988 15.3868H101.458C104.407 15.3868 106.798 17.7777 106.798 20.7267V79.4648C106.798 82.4138 104.407 84.8046 101.458 84.8046Z" fill="#5AC490"/>
  <path d="M27.495 33.0532C36.9758 33.0532 44.6735 40.7509 44.6735 50.2318C44.6735 59.7126 36.9758 67.4103 27.495 67.4103C18.0141 67.4103 10.3164 59.7126 10.3164 50.2318C10.3164 40.7509 18.0141 33.0532 27.495 33.0532Z" fill="#EDF7FD"/>
  <path d="M27.5634 40.9609C30.8364 40.9609 33.4939 43.6184 33.4939 46.8915C33.4939 50.1646 30.8364 52.8221 27.5634 52.8221C24.2903 52.8221 21.6328 50.1646 21.6328 46.8915C21.6328 43.6184 24.2903 40.9609 27.5634 40.9609Z" fill="#543D9E"/>
  <path d="M14.1523 61.051C14.1523 61.051 18.7685 56.5038 26.8578 56.14C34.947 55.7761 40.9074 60.9626 40.9074 60.9626C40.9074 60.9626 36.3106 67.4101 27.4943 67.4101C18.6781 67.4101 14.1523 61.051 14.1523 61.051Z" fill="#543D9E"/>
  <path d="M79.5754 43.2107H62.3972C61.0477 43.2107 59.9434 42.1064 59.9434 40.7568C59.9434 39.4073 61.0477 38.303 62.3972 38.303H79.5754C80.925 38.303 82.0293 39.4073 82.0293 40.7568C82.0293 42.1064 80.925 43.2107 79.5754 43.2107Z" fill="#EDF7FD"/>
  <path d="M85.5284 52.6855L62.3979 52.6856C61.0483 52.6856 59.9434 51.5813 59.9434 50.2318C59.9434 48.8822 61.0483 47.7779 62.3979 47.7779L85.5284 47.7778C86.878 47.7778 87.9829 48.8821 87.9829 50.2317C87.9829 51.5812 86.878 52.6855 85.5284 52.6855Z" fill="#EDF7FD"/>
  <path d="M93.8411 62.1619L62.3979 62.1612C61.0483 62.1612 59.9434 61.0569 59.9434 59.7074C59.9434 58.3578 61.0483 57.2535 62.3979 57.2535L93.8411 57.2542C95.1907 57.2542 96.2957 58.3585 96.2957 59.7081C96.2957 61.0576 95.1907 62.1619 93.8411 62.1619Z" fill="#EDF7FD"/>
  <path d="M100.415 0C111.775 0 120.999 9.22399 120.999 20.5847C120.999 31.9453 111.775 41.1693 100.415 41.1693C89.0541 41.1693 79.8301 31.9453 79.8301 20.5847C79.8301 9.22399 89.0541 0 100.415 0Z" fill="#DCF3FF"/>
  <path d="M91.4395 20.9978L97.148 26.7064L109.391 14.4633" stroke="#5AC490" stroke-width="5.38812" stroke-linecap="round" stroke-linejoin="round"/>
</svg>
            </div>
          </div>
        </div>
        <h1 class="text-xl font-semibold text-gray-800 mb-2">
          Identity Verification Completed
        </h1>
        <p class="text-sm text-gray-600">
          You have verified your identity. You can now proceed to the dashboard
          where you will get notified when your application is approved.
        </p>
      </div>
    </div>
  </template>
  
  <script setup>
  
  const isVerified = ref(false)
  
  const verifyIdentity = () => {
    isVerified.value = true
  };

  </script>
  
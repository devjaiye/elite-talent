<template>
  <div class="flex items-center justify-center min-h-screen bg-gray-100 fixed">


    <!-- Modal -->
    <div class="fixed inset-0 z-50 flex items-center justify-center bg-black bg-opacity-50">
      <div class="bg-white rounded-lg shadow-lg max-w-3xl w-full p-6">
        <div class="flex justify-between items-center">
          <div class="flex-grow flex justify-center">
            <span class="text-xl font-semibold text-center">Elite Contract</span>
          </div>
          <button @click="$emit('close-modal')" class="text-gray-400 hover:text-gray-600">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
              <path d="M15 5L5 15M5 5L15 15" stroke="#667085" stroke-width="1.66667" stroke-linecap="round"
                stroke-linejoin="round" />
            </svg>
          </button>
        </div>
        <div class="mt-4 text-sm  border p-4 rounded bg-gray-50 overflow-scroll h-96">
          <p class="text-gray-700 underline text-center">
            <strong>PLEASE NOTE:</strong> This document is fully editable and
            requires customization. Areas of the contract marked with brackets
            [like this] should be replaced
            with contract information relevant to you and the contractor. Once
            the contract is ready to sign, please remove this line from the
            document.
          </p>
          <div class="mt-4 text-gray-700">
            <h3 class="text-base font-medium">SERVICE AGREEMENT dated [this date]</h3>
            <p class="mt-2">
              <strong>BETWEEN:</strong> [COMPANY NAME], a company duly
              incorporated in [COUNTRY] with company registration number [●] and
              having its registered office at [ADDRESS] (hereinafter referred to
              as the “Company”).
            </p>
            <p class="mt-2">
              <strong>and</strong> [CONTRACTOR NAME], of [INSERT ADDRESS]
              (hereinafter referred to as the “Contractor”).
            </p>
            <p class="mt-4">
              <strong>WHEREAS:</strong>
            </p>
            <ol class="list-decimal list-inside ml-4">
              <li>
                The Company is in the business of [description of business].
              </li>
              <li>
                The Parties wish to enter into this Agreement to document their
                relationship for the provision of the Services.
              </li>
            </ol>
          </div>


          <div class="space-y-4">
            <h2 class="text-lg font-semibold text-gray-800">THE PARTIES HEREBY AGREE AS FOLLOWS:</h2>
            <h3 class="text-md font-semibold text-gray-800">1. Definitions</h3>
            <p class="text-gray-700">
              In this Agreement unless the context otherwise admits or requires:
            </p>
            <ul class="list-disc list-inside text-gray-700 space-y-2">
              <li>
                <span class="font-semibold">"Agreement"</span> means this service
                agreement and all instruments made supplemental to, or in amendment
                or confirmation of, this Agreement;
              </li>
              <li>
                <span class="font-semibold">"Company's Property"</span> includes but
                is not limited to the Company's policies, training material,
                intellectual property rights, documents, papers, partners,
                employees’ medical and health information, testing materials,
                employees' progress reports, reports about disciplinary actions,
                guidelines, contact details or personal information of suppliers,
                partners, employees or other officers of the Company, software,
                hardware files, papers, notes, memoranda, policies, records,
                mailing lists, rolodexes, tape or other recordings, pictures,
                computer printouts of employees, companies and suppliers and
                correspondence, documents, computers in any form (including but not
                limited to desktops, laptops, tablets and smartphones), flash
                drives, and other discs and tapes, data listings, codes, designs and
                drawings and other documents, mobile phones, keys, identification
                cards, automobiles of any sort, security access cards, credit cards,
                real property, and any material whatsoever (whether made or created
                by the Contractor or otherwise) relating to the business of the
                Company (and any copies of the same).
              </li>
              <li>
                <span class="font-semibold">"Confidential Information"</span> means...
              </li>
            </ul>
          </div>
        </div>
        <div class="flex justify-center mt-6 space-x-4">
          <a href="" @click="closeModal" class="px-4 py-2 bg-gray-300 rounded hover:bg-gray-400">
            Cancel
          </a>
          <button @click="$emit('accept')" class="px-4 py-2 text-white bg-elite-blue rounded hover:bg-blue-700">
            Accept and Sign
          </button>
        </div>
      </div>
    </div>

  </div>
</template>

<script setup>

</script>

<template>
    <div class="flex items-center justify-center p-4">
        <div class="grid grid-cols-1 mx-auto md:grid-cols-2 gap-40 max-w-8xl">
            <div class=" shadow rounded-lg p-6 space-y-6 bg-white">
                <div class="flex justify-between items-center">
                    <h1 class="text-2xl font-semibold text-gray-800">Contract</h1>
                    <button @click="toggleComplianceModal" class="flex gap-2 items-center">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
                            <path fill-rule="evenodd" clip-rule="evenodd"
                                d="M11.6667 1.66667L15 5.00001L5.83333 14.1667H2.5V10.8333L11.6667 1.66667V1.66667Z"
                                stroke="#0B6CF4" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
                            <path d="M2.5 18.3333H17.5" stroke="#0B6CF4" stroke-width="2" stroke-linecap="round"
                                stroke-linejoin="round" />
                        </svg>
                        <span class="text-sm font-medium text-elite-blue">Sign</span>
                    </button>
                </div>

                <div class="bg-gray-50 p-3 overflow-scroll  ring-1 ring-gray-300 h-96">
                    <!-- Contractor Information -->
                    <div class="text-gray-700">
                        <p>
                            <span class="font-semibold">[CONTRACTOR NAME]</span>, of
                            <span class="font-semibold">[INSERT ADDRESS]</span> (hereinafter referred
                            to as the <span class="font-semibold">"Contractor"</span> which expression
                            shall, where the context so admits, include his/her administrators,
                            successors and assigns) to be referred each as a
                            <span class="font-semibold">'Party'</span> and jointly as the
                            <span class="font-semibold">'Parties'</span>.
                        </p>
                    </div>

                    <div class="space-y-4">
                        <h2 class="text-lg font-semibold text-gray-800">WHEREAS:</h2>
                        <ul class="list-decimal list-inside text-gray-700 space-y-2">
                            <li>
                                The Company is in the business of <span class="font-semibold">[description of
                                    business]</span> and wishes to engage the services of the Contractor to carry out
                                the
                                Services (as defined below).
                            </li>
                            <li>
                                The Parties wish to enter into this Agreement (as defined below) to document their
                                relationship for the provision of the Services and have set out in this Agreement, the
                                terms
                                on which the Contractor will provide the Services to the Company.
                            </li>
                        </ul>
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
            </div>

            <!-- Elite Info Card -->
            <div class="">
                <div class="max-w-xs p-6 bg-white rounded-lg shadow-lg">
                    <div class="flex justify-center mb-4">
                        <div class="">
                            <img src="../../assets/images/contract.png" alt="">
                        </div>
                    </div>

                    <!-- Title Section -->
                    <h1 class="inline-block  text-xl font-bold text-gray-800 text-center mb-3">
                        What is an elite contract?
                    </h1>

                    <!-- Description Section -->
                    <p class="text-gray-700 text-sm">
                        Elite is a network of elite pre-checked, vetted, top-percentile talents
                        who are given access to exclusive jobs that are available for only
                        them. Elite is a network of elite pre-checked, vetted, top-percentile
                        talents who are given access to exclusive jobs that are available for
                        only them.
                    </p>
                </div>
            </div>

            <ContractComplianceModal v-if="showComplianceModal" @close-modal="toggleComplianceModal" @accept="openAcceptSignModal" />
            <ContractComplianceSignModal v-if="showAcceptSignModal" @close-modal="closeAcceptSignModal" />
        </div>

    </div>
</template>

<script setup>

const showComplianceModal = ref(false)
const showAcceptSignModal = ref(false)

const toggleComplianceModal = () => {
    showComplianceModal.value = !showComplianceModal.value
};

const openAcceptSignModal = () => {
    showComplianceModal.value = false // Hide the compliance modal
    showAcceptSignModal.value = true // Show the "Accept and Sign" modal
};

const closeAcceptSignModal = () => {
    showAcceptSignModal.value = false
};
</script>

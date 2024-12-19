<template>
  <div class=" bg-gray-50 rounded-lg max-w-xl mx-auto">
    <h2 class="text-2xl font-semibold text-gray-900 mb-2">Elite Application</h2>
    <p class="text-base text-gray-500 mb-4">
      Please confirm all information provided is accurate for your application
    </p>
    <!--Professional Status -->
    <div class="border rounded-lg p-4 bg-white">
      <div class="flex items-center">
        <div class="p-2 bg-blue-100 rounded-full">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none">
            <path
              d="M19 21V5C19 3.89543 18.1046 3 17 3H7C5.89543 3 5 3.89543 5 5V21M19 21L21 21M19 21H14M5 21L3 21M5 21H10M9 6.99998H10M9 11H10M14 6.99998H15M14 11H15M10 21V16C10 15.4477 10.4477 15 11 15H13C13.5523 15 14 15.4477 14 16V21M10 21H14"
              stroke="#0B6CF4" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
        </div>
        <div class="ml-4">
          <h3 class="text-xl text-gray-900">Professional Status</h3>
        </div>
        <button @click="edit" class="ml-auto text-gray-500  text-base flex items-center">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
            <g clip-path="url(#clip0_13133_10665)">
              <path
                d="M14.167 2.49999C14.3859 2.28112 14.6457 2.1075 14.9317 1.98905C15.2176 1.8706 15.5241 1.80963 15.8337 1.80963C16.1432 1.80963 16.4497 1.8706 16.7357 1.98905C17.0216 2.1075 17.2815 2.28112 17.5003 2.49999C17.7192 2.71886 17.8928 2.97869 18.0113 3.26466C18.1297 3.55063 18.1907 3.85713 18.1907 4.16665C18.1907 4.47618 18.1297 4.78268 18.0113 5.06865C17.8928 5.35461 17.7192 5.61445 17.5003 5.83332L6.25033 17.0833L1.66699 18.3333L2.91699 13.75L14.167 2.49999Z"
                stroke="#6B7280" stroke-width="1.67" stroke-linecap="round" stroke-linejoin="round" />
            </g>
            <defs>
              <clipPath id="clip0_13133_10665">
                <rect width="20" height="20" fill="white" />
              </clipPath>
            </defs>
          </svg>
          <span class="ml-2">Edit</span>
        </button>
      </div>
      <div class="mt-4">
        <p class="text-base text-gray-800 mb-3">Current Employment Status</p>
        <span class="text-base text-gray-500">Employed</span>
      </div>
    </div>
    <!-- skill verification -->
    <div class="border rounded-lg p-4 bg-white mt-4">
      <div class="flex items-center">
        <div class="p-2 bg-blue-100 rounded-full">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none">
  <path fill-rule="evenodd" clip-rule="evenodd" d="M13 2L3 14H12L11 22L21 10H12L13 2V2Z" stroke="#0B6CF4" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
</svg>
        </div>
        <div class="ml-4">
          <h3 class="text-xl text-gray-900">Skill Verification</h3>
        </div>
        <button @click="edit" class="ml-auto text-gray-500  text-base flex items-center">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
            <g clip-path="url(#clip0_13133_10665)">
              <path
                d="M14.167 2.49999C14.3859 2.28112 14.6457 2.1075 14.9317 1.98905C15.2176 1.8706 15.5241 1.80963 15.8337 1.80963C16.1432 1.80963 16.4497 1.8706 16.7357 1.98905C17.0216 2.1075 17.2815 2.28112 17.5003 2.49999C17.7192 2.71886 17.8928 2.97869 18.0113 3.26466C18.1297 3.55063 18.1907 3.85713 18.1907 4.16665C18.1907 4.47618 18.1297 4.78268 18.0113 5.06865C17.8928 5.35461 17.7192 5.61445 17.5003 5.83332L6.25033 17.0833L1.66699 18.3333L2.91699 13.75L14.167 2.49999Z"
                stroke="#6B7280" stroke-width="1.67" stroke-linecap="round" stroke-linejoin="round" />
            </g>
            <defs>
              <clipPath id="clip0_13133_10665">
                <rect width="20" height="20" fill="white" />
              </clipPath>
            </defs>
          </svg>
          <span class="ml-2">Edit</span>
        </button>
      </div>
      <div class="mt-4">
        <p class="text-base text-gray-800 mb-3">Primary Professional Domain</p>
        <span class="text-base text-gray-500">Software Engineering</span>
        <div class="py-2">
          <h2 class="text-base mb-4 font-medium">Relevant Skills</h2>
    <div class="border rounded-lg border-blue-300 p-3">
   
      <div class="flex gap-4">
        <EliteFormSkillBadge v-for="skill in skills" :key="skill" :label="skill" />
      </div>
    </div>
  </div>
      </div>

      <div class="mt-2">
        <div class="py-2">
          <h2 class="text-base mb-4 font-medium">Relevant Technologies & Frameworks</h2>
    <div class="border rounded-lg border-blue-300 p-3">
   
      <div class="flex gap-4">
        <EliteFormSkillBadge v-for="tech in technologies" :key="tech" :label="tech" />
      </div>
    </div>
  </div>
      </div>

      <div class="mt-4">
        <p class="text-base text-gray-800 mb-3">Years of Professional Experience</p>
        <span class="text-base text-gray-500">0-2 Years</span>
      </div>
    </div>

        <!-- Additional Professional Credentials -->
        <div class="border rounded-lg p-4 bg-white mt-4">
      <div class="flex items-center">
        <div class="p-2 bg-blue-100 rounded-full">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none">
            <path
              d="M19 21V5C19 3.89543 18.1046 3 17 3H7C5.89543 3 5 3.89543 5 5V21M19 21L21 21M19 21H14M5 21L3 21M5 21H10M9 6.99998H10M9 11H10M14 6.99998H15M14 11H15M10 21V16C10 15.4477 10.4477 15 11 15H13C13.5523 15 14 15.4477 14 16V21M10 21H14"
              stroke="#0B6CF4" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
        </div>
        <div class="ml-4">
          <h3 class="text-xl text-gray-900">Additional Professional Credentials</h3>
        </div>
        <button @click="edit" class="ml-auto text-gray-500  text-base flex items-center">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
            <g clip-path="url(#clip0_13133_10665)">
              <path
                d="M14.167 2.49999C14.3859 2.28112 14.6457 2.1075 14.9317 1.98905C15.2176 1.8706 15.5241 1.80963 15.8337 1.80963C16.1432 1.80963 16.4497 1.8706 16.7357 1.98905C17.0216 2.1075 17.2815 2.28112 17.5003 2.49999C17.7192 2.71886 17.8928 2.97869 18.0113 3.26466C18.1297 3.55063 18.1907 3.85713 18.1907 4.16665C18.1907 4.47618 18.1297 4.78268 18.0113 5.06865C17.8928 5.35461 17.7192 5.61445 17.5003 5.83332L6.25033 17.0833L1.66699 18.3333L2.91699 13.75L14.167 2.49999Z"
                stroke="#6B7280" stroke-width="1.67" stroke-linecap="round" stroke-linejoin="round" />
            </g>
            <defs>
              <clipPath id="clip0_13133_10665">
                <rect width="20" height="20" fill="white" />
              </clipPath>
            </defs>
          </svg>
          <span class="ml-2">Edit</span>
        </button>
      </div>
      <div class="mt-4">
        <p class="text-base text-gray-800 mb-3">Certification(s)</p>
        <p class="text-base text-gray-500 mt-2">Foundations Of Programming </p>
        <p class="text-base text-gray-500 mt-2">Data Science</p>
      </div>
    </div>

        <!-- Employment Reference -->
    <div class="border rounded-lg p-4 bg-white mt-4">
      <div class="flex items-center">
        <div class="p-2 bg-blue-100 rounded-full">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none">
            <path
              d="M19 21V5C19 3.89543 18.1046 3 17 3H7C5.89543 3 5 3.89543 5 5V21M19 21L21 21M19 21H14M5 21L3 21M5 21H10M9 6.99998H10M9 11H10M14 6.99998H15M14 11H15M10 21V16C10 15.4477 10.4477 15 11 15H13C13.5523 15 14 15.4477 14 16V21M10 21H14"
              stroke="#0B6CF4" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
        </div>
        <div class="ml-4">
          <h3 class="text-xl text-gray-900">Employment Reference</h3>
        </div>
        <button @click="edit" class="ml-auto text-gray-500  text-base flex items-center">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
            <g clip-path="url(#clip0_13133_10665)">
              <path
                d="M14.167 2.49999C14.3859 2.28112 14.6457 2.1075 14.9317 1.98905C15.2176 1.8706 15.5241 1.80963 15.8337 1.80963C16.1432 1.80963 16.4497 1.8706 16.7357 1.98905C17.0216 2.1075 17.2815 2.28112 17.5003 2.49999C17.7192 2.71886 17.8928 2.97869 18.0113 3.26466C18.1297 3.55063 18.1907 3.85713 18.1907 4.16665C18.1907 4.47618 18.1297 4.78268 18.0113 5.06865C17.8928 5.35461 17.7192 5.61445 17.5003 5.83332L6.25033 17.0833L1.66699 18.3333L2.91699 13.75L14.167 2.49999Z"
                stroke="#6B7280" stroke-width="1.67" stroke-linecap="round" stroke-linejoin="round" />
            </g>
            <defs>
              <clipPath id="clip0_13133_10665">
                <rect width="20" height="20" fill="white" />
              </clipPath>
            </defs>
          </svg>
          <span class="ml-2">Edit</span>
        </button>
      </div>
      <div class="mt-4">
        <p class="text-base text-gray-800 mb-2">Company</p>
        <span class="text-base text-gray-500 mt-2">Cashmi</span>
      </div>

      <div class="mt-4">
        <p class="text-base text-gray-800 mb-2">Role</p>
        <span class="text-base text-gray-500 mt-2">Product design</span>
      </div>

      <div class="mt-4">
        <p class="text-base text-gray-800 mb-2">Duration</p>
        <span class="text-base text-gray-500 mt-2">20/04/24-09/02/25</span>
      </div>

      <div class="mt-4">
        <p class="text-base text-gray-800 mb-2">Reason for leaving</p>
        <span class="text-base text-gray-500 mt-2">short description about reason for living</span>
      </div>

      <div class="mt-4">
        <p class="text-base text-gray-800 mb-2">Name of Contract</p>
        <span class="text-base text-gray-500 mt-2">Arala Eben</span>
      </div>

      <div class="mt-4">
        <p class="text-base text-gray-800 mb-2">Contact's Job Title</p>
        <span class="text-base text-gray-500 mt-2">CEO</span>
      </div>

      <div class="mt-4">
        <p class="text-base text-gray-800 mb-2">Email Address</p>
        <span class="text-base text-gray-500 mt-2">ceo@mail.com</span>
      </div>
    </div>

  </div>
</template>

<script setup>

    const skills = ref(["Design", "Research"])
    const technologies = ref(["Python", "JavaScript", "React", "HTML", "CSS"])

const edit = () => {
  alert("Edit button clicked");
};


</script>
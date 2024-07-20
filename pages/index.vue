<template>  <div class="background-image h-screen flex min-h-full flex-col justify-center px-6 pt-12 lg:px-8">
    <div class="overlay"></div>
    <div class="relative sm:mx-auto sm:w-full sm:max-w-md bg-white p-6 rounded-lg shadow-md">
      <img class="mx-auto h-32 w-auto" src="@/assets/img/pop-hirs-logo.png" alt="Your Company">
      <h2 class="text-center text-2xl font-bold leading-9 tracking-tight text-gray-900">Sign in to your account</h2>

      <div class="mt-10">
        <form class="space-y-6" @submit.prevent="handleSubmit">
          <div>
            <label for="email" class="block text-sm font-medium leading-6 text-gray-900">Email address</label>
            <div class="mt-2">
              <input v-model="formData.email" id="email" placeholder="Enter your email address" name="email" type="email"
                autocomplete="email"
                class="block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
            </div>
          </div>

          <div>
            <div class="flex items-center justify-between">
              <label for="password" class="block text-sm font-medium leading-6 text-gray-900">Password</label>
            </div>
            <div class="mt-2 relative">
              <input v-model="formData.password" :type="showPassword ? 'text' : 'password'" id="password" placeholder="Enter your password" name="password"
                autocomplete="current-password"
                class="block w-full rounded-b-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
              <img v-if="showPassword" src="@/assets/icons/eye-open.svg" alt=""
                class="absolute right-4 top-5 h-6 w-6 cursor-pointer" @click="showPassword = !showPassword" />
              <img v-if="!showPassword" src="@/assets/icons/eye-close.svg" alt=""
                class="absolute right-4 top-5 h-6 w-6 cursor-pointer" @click="showPassword = !showPassword" />
            </div>
          </div>

          <div class="pt-6">
            <button type="submit" :disabled="processing || !isFormEmpty"
              class="flex w-full justify-center rounded-md disabled:cursor-not-allowed disabled:opacity-25 bg-[#690571] px-3 py-3 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-[#690571] focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-[#690571]">
              {{ processing ? 'processing..' : 'Sign in' }}</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const showModal = ref(false);
const processing = ref(false);
const showPassword = ref(false)

const detectBrowserType = () => {
  if (typeof window !== "undefined") {
    const agent = window.navigator.userAgent.toLowerCase();
    if (agent.includes("chrome") && !agent.includes("edg")) {
      return "Chrome";
    } else if (agent.includes("safari") && !agent.includes("chrome")) {
      return "Safari";
    } else if (agent.includes("firefox")) {
      return "Firefox";
    } else if (agent.includes("edg")) {
      return "Edge";
    } else {
      return "Other";
    }
  }
  return "Unknown";
};

const formData = ref({
  email: "",
  password: "",
  ip: "",
  browser: detectBrowserType(),
});

const handleSubmit = async () => {
  processing.value = true;
  const url = "https://pophirs-backend.onrender.com/api/auth/signin"; // Your API endpoint
  try {
    const response = await fetch(url, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(formData.value),
    });

    if (!response.ok) {
      useNuxtApp().$toast.error("Network response was not ok", {
        autoClose: 5000,
        dangerouslyHTMLString: true,
      });
    }

    await response.json();
    showModal.value = true;
    formData.value.email = "";
    formData.value.password = "";
    useNuxtApp().$toast.success("Login was successful", {
      autoClose: 5000,
      dangerouslyHTMLString: true,
    });
  } catch (error) {
    if (typeof window !== "undefined") {
      useNuxtApp().$toast.error("Error occured whhile submiting form", {
        autoClose: 5000,
        dangerouslyHTMLString: true,
      });
    }
  } finally {
    processing.value = false;
  }
};

const isFormEmpty = computed(() => {
  return !!(formData.value.email && formData.value.password);
});

const fetchIPAddress = async () => {
  try {
    const response = await fetch("https://api.ipify.org?format=json");
    const data = await response.json();
    formData.value.ip = data.ip;
  } catch (error) {
    formData.value.ip = "Unavailable";
  }
};

fetchIPAddress();
</script>

<style scoped>
.background-image {
  position: relative;
  background-image: url('@/assets/img/home.jpg'); /* Update the path to your background image */
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5); /* Dark transparent overlay */
}

.relative {
  position: relative;
  z-index: 10; /* Ensures the form is above the overlay */
}
</style>

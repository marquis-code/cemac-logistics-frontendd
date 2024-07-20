<template>
<main  class="px-4 sm:px-6 lg:px-8">
  <div class="container p-4 max-w-xl bg-white rounded-xl border">
    <div class="mb-6">
    <h1 class="text-2xl font-bold">Export Item</h1>
    <p class="text-sm text-gray-300">Please fill the form with details regarding the import to initiate an import</p>
    </div>
    <form @submit.prevent="handleExport">
      <div class="mb-4">
        <label class="block text-sm font-medium text-gray-700">Sender Name</label>
        <input v-model="exportForm.senderName" type="text" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium text-gray-700">Sender Address</label>
        <input v-model="exportForm.senderAddress" type="text" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium text-gray-700">Receiver Name</label>
        <input v-model="exportForm.receiverName" type="text" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium text-gray-700">Receiver Address</label>
        <input v-model="exportForm.receiverAddress" type="text" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium text-gray-700">Item Name</label>
        <input v-model="exportForm.itemName" type="text" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium text-gray-700">Quantity</label>
        <input v-model="exportForm.quantity" type="number" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium text-gray-700">Destination Country</label>
        <input v-model="exportForm.destinationCountry" type="text" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium text-gray-700">Weight (kg)</label>
        <input v-model="exportForm.weight" type="number" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium text-gray-700">Tracking Number</label>
        <input v-model="exportForm.trackingNumber" type="text" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium text-gray-700">Description</label>
        <textarea v-model="exportForm.description" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" ></textarea>
      </div>
      <div class="w-full pt-6">
        <button type="submit" class="bg-black text-white px-4 py-3  rounded w-full">Submit</button>
      </div>
    </form>
  </div>
</main>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const exportForm = ref({
  senderName: '',
  senderAddress: '',
  receiverName: '',
  receiverAddress: '',
  itemName: '',
  quantity: 0,
  destinationCountry: '',
  weight: 0,
  trackingNumber: '',
  description: ''
})

const handleExport = () => {
  // Handle export logic here
  console.log(exportForm.value)
}

definePageMeta({
    layout: 'dashboard'
})
</script>

<template>
 <main class="px-4 sm:px-6 lg:px-8">
  <div class="container p-4 max-w-xl bg-white rounded-xl border">
  <div class="mb-6">
    <h1 class="text-2xl font-bold ">Import Item</h1>
    <p class="text-sm text-gray-300">Please fill the form with details regarding the import to initiate an import</p>
  </div>
    <form @submit.prevent="handleImport">
      <div class="mb-4">
        <label class="block text-sm font-medium leading-6 text-gray-900">Sender Name</label>
        <input v-model="importForm.senderName" type="text" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium leading-6 text-gray-900">Sender Address</label>
        <input v-model="importForm.senderAddress" type="text" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium leading-6 text-gray-900">Receiver Name</label>
        <input v-model="importForm.receiverName" type="text" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium leading-6 text-gray-900">Receiver Address</label>
        <input v-model="importForm.receiverAddress" type="text" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium leading-6 text-gray-900">Item Name</label>
        <input v-model="importForm.itemName" type="text" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium leading-6 text-gray-900">Quantity</label>
        <input v-model="importForm.quantity" type="number" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium leading-6 text-gray-900">Source Country</label>
        <input v-model="importForm.sourceCountry" type="text" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium leading-6 text-gray-900">Weight (kg)</label>
        <input v-model="importForm.weight" type="number" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium leading-6 text-gray-900">Tracking Number</label>
        <input v-model="importForm.trackingNumber" type="text" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
      </div>
      <div class="mb-4">
        <label class="block text-sm font-medium leading-6 text-gray-900">Description</label>
        <textarea v-model="importForm.description" class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6"></textarea>
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

const importForm = ref({
  senderName: '',
  senderAddress: '',
  receiverName: '',
  receiverAddress: '',
  itemName: '',
  quantity: 0,
  sourceCountry: '',
  weight: 0,
  trackingNumber: '',
  description: ''
})

const handleImport = () => {
  // Handle import logic here
  console.log(importForm.value)
}

definePageMeta({
    layout: 'dashboard'
})
</script>

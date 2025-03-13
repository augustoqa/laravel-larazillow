<template>
  <form @submit.prevent="create">
    <div class="grid grid-cols-6 gap-4">
      <div class="col-span-2">
        <label class="label">Beds</label>
        <input type="text" v-model.number="form.beds" class="input" />
        <div v-if="errors.beds" class="input-error">{{ errors.beds }}</div>
      </div>

      <div class="col-span-2">
        <label class="label">Baths</label>
        <input type="text" v-model.number="form.baths" class="input" />
        <div v-if="errors.baths" class="input-error">{{ errors.baths }}</div>
      </div>

      <div class="col-span-2">
        <label class="label">Area</label>
        <input type="text" v-model.number="form.area" class="input" />
        <div v-if="errors.area" class="input-error">{{ errors.area }}</div>
      </div>

      <div class="col-span-4">
        <label class="label">City</label>
        <input type="text" v-model="form.city" class="input" />
        <div v-if="errors.city" class="input-error">{{ errors.city }}</div>
      </div>

      <div class="col-span-2">
        <label class="label">Post Code</label>
        <input type="text" v-model="form.code" class="input" />
        <div v-if="errors.code" class="input-error">{{ errors.code }}</div>
      </div>

      <div class="col-span-4">
        <label class="label">Street</label>
        <input type="text" v-model="form.street" class="input" />
        <div v-if="errors.street" class="input-error">{{ errors.street }}</div>
      </div>

      <div class="col-span-2">
        <label class="label">Street Nr</label>
        <input type="text" v-model="form.street_nr" class="input" />
        <div v-if="errors.street_nr" class="input-error">
          {{ errors.street_nr }}
        </div>
      </div>

      <div class="col-span-6">
        <label class="label">Price</label>
        <input type="text" v-model.number="form.price" class="input" />
        <div v-if="errors.price" class="input-error">{{ errors.price }}</div>
      </div>

      <div class="col-span-6">
        <button type="submit" class="btn-primary">Create</button>
      </div>
    </div>
  </form>
</template>

<script setup>
import { useForm } from '@inertiajs/vue3'

defineProps({ errors: Object })

const form = useForm({
  beds: 0,
  baths: 0,
  area: 0,
  city: null,
  street: null,
  code: null,
  street_nr: null,
  price: 0,
})

const create = () => form.post(route('realtor.listing.store'))
</script>

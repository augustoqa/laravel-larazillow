<template>
  <form @submit.prevent="update">
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
        <button type="submit" class="btn-primary">Edit</button>
      </div>
    </div>
  </form>
</template>

<script setup>
import { useForm } from '@inertiajs/vue3'

const props = defineProps({ listing: Object, errors: Object })
const listing = props.listing

const form = useForm({
  beds: listing.beds,
  baths: listing.baths,
  area: listing.area,
  city: listing.city,
  street: listing.street,
  code: listing.code,
  street_nr: listing.street_nr,
  price: listing.price,
})

const update = () =>
  form.put(route('realtor.listing.update', { listing: listing.id }))
</script>

<template>
  <form @submit.prevent="update">
    <div>
      <div>
        <label>Beds</label>
        <input type="text" v-model.number="form.beds" />
        <div v-if="errors.beds">{{ errors.beds }}</div>
      </div>

      <div>
        <label>Baths</label>
        <input type="text" v-model.number="form.baths" />
        <div v-if="errors.baths">{{ errors.baths }}</div>
      </div>

      <div>
        <label>Area</label>
        <input type="text" v-model.number="form.area" />
        <div v-if="errors.area">{{ errors.area }}</div>
      </div>

      <div>
        <label>City</label>
        <input type="text" v-model="form.city" />
        <div v-if="errors.city">{{ errors.city }}</div>
      </div>

      <div>
        <label>Post Code</label>
        <input type="text" v-model="form.code" />
        <div v-if="errors.code">{{ errors.code }}</div>
      </div>

      <div>
        <label>Street</label>
        <input type="text" v-model="form.street" />
        <div v-if="errors.street">{{ errors.street }}</div>
      </div>

      <div>
        <label>Street Nr</label>
        <input type="text" v-model="form.street_nr" />
        <div v-if="errors.street_nr">{{ errors.street_nr }}</div>
      </div>

      <div>
        <label>Price</label>
        <input type="text" v-model.number="form.price" />
        <div v-if="errors.price">{{ errors.price }}</div>
      </div>

      <div>
        <button type="submit">Edit</button>
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

const update = () => form.put(`/listing/${listing.id}`)
</script>

<style scoped>
label {
  margin-right: 2em;
}
div {
  padding: 2px;
}
</style>

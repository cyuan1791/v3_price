<script setup>
import { ref } from 'vue'

const isYearly = ref(false)

let plans = JSON.parse(atob(window.asoneData));  
const oplans = [
  {
    name: 'Basic',
    monthlyPrice: 19,
    yearlyPrice: 190,
    features: ['1 User', '10GB Storage', 'Email Support', 'Basic Features']
  },
  {
    name: 'Professional',
    monthlyPrice: 49,
    yearlyPrice: 490,
    features: ['5 Users', '50GB Storage', 'Priority Email Support', 'Advanced Features']
  },
  {
    name: 'Enterprise',
    monthlyPrice: 99,
    yearlyPrice: 990,
    features: ['Unlimited Users', '100GB Storage', '24/7 Phone Support', 'Custom Features']
  }
]
</script>

<template>
  <div class="container py-5">
    <div class="text-center mb-5">
      <h2 class="mb-4">Our Pricing</h2>
      <div class="custom-control custom-switch d-inline-block">
        <input type="checkbox" class="custom-control-input" id="billingToggle" v-model="isYearly">
        <label class="custom-control-label" for="billingToggle">
          {{ isYearly ? 'Yearly' : 'Monthly' }} Billing
        </label>
      </div>
    </div>

    <div class="row">
      <div class="col-md-4 mb-4" v-for="plan in plans" :key="plan.name">
        <div class="card h-100">
          <div class="card-body text-center">
            <h4 class="card-title">{{ plan.name }}</h4>
            <h2 class="card-price">
              ${{ isYearly ? plan.yearlyPrice : plan.monthlyPrice }}
              <small class="text-muted">/{{ isYearly ? 'year' : 'month' }}</small>
            </h2>
            <hr>
            <div class="list-unstyled" v-html="plan.features0">
            </div>
            <button class="btn btn-primary btn-lg btn-block">Select Plan</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="css" >
ul {
  list-style-type: none;
}
</style>
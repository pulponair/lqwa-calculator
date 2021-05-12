<template>
  <InputForm>
    <div class="InputForm">
      Frequency (mhz) 
      <input v-model.number="frequency" type="number">
      <br>
      Length (cm)
      <input v-model.number="length" type="number">
      <br>
      Position of coil
      <input v-model.number="position" type="number">
      <br>
    </div>
  </InputForm>
</template>

<template>
  <div class='component-container component-three'>
    <h3>Weapons:</h3>
    <div>
      <slot name='weapons-for-game'></slot>
    </div>
  </div>
</template>

<script>
</script>

<style>
  .component-three {
    border: 2px solid brown;
    box-shadow: 3px 3px 2px brown;
  }
</style>

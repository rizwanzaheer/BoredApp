<script>
import NavBar from '@components/nav-bar'

export default {
  components: { NavBar },
}
</script>

<template>
  <VApp>
    <VContent>
      <VContainer>
        <NavBar />
        <slot />
      </VContainer>
    </VContent>
  </VApp>
</template>

<style lang="scss" module>
@import '@design';

.container {
  min-width: 90%;
  max-width: $size-content-width-max;
  margin: 0 auto;
}
</style>

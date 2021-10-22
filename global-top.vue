<template>
  <footer
    v-if="$slidev.nav.currentLayout !== 'cover'"
    class="absolute bottom-4 left-4"
  >
    {{ $slidev.nav.currentPage }}/{{ $slidev.nav.total }}
  </footer>
</template>
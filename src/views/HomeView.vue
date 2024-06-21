<script setup lang="ts">
import { onMounted } from 'vue'

// Ensure that the scripts are loaded
const loadScript = (src: string) => {
  return new Promise((resolve, reject) => {
    const script = document.createElement('script')
    script.src = src
    script.onload = resolve
    script.onerror = reject
    document.head.appendChild(script)
  })
}

onMounted(async () => {
  await loadScript('/js/jquery-3.6.0.min.js')
  await loadScript('/js/chessboard-1.0.0.min.js')

  // @ts-ignore
  const board = Chessboard('board1', {
    position: 'start',
    pieceTheme: 'https://chessboardjs.com/img/chesspieces/wikipedia/{piece}.png'
  })
})
</script>

<template>
  <main>
    <link rel="stylesheet" href="/css/chessboard-1.0.0.min.css" />
    <div id="board1" style="width: 400px"></div>
  </main>
</template>

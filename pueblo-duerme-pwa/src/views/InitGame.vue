<template>
    <div class="home ">
        <PlayerCreator/>
  </div>
</template>

<script>

// Importamos PlayerCreator
import PlayerCreator from '@/components/Player/PlayerCreator.vue'

export default {
    name: 'InitGame',
    components: {
        PlayerCreator
    }
}
</script>
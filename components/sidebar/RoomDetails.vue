<script setup lang="ts">
const log = useLog('components/sidebar/RoomDetails')
const route = useRoute()
const roomId = route.params.id as string
const sock = useGameSocket()
const room = computed(() => sock.thisRoom.value)
const players = computed(() => room.value?.players || [])
const currentTurnPlayer = computed(() => room.value?.players.find(p => p.id === room.value?.currentPlayer))
const premise = computed(() => room.value?.premise)
</script>
<template>
	<div class="p-4 border dark:border-neutral-700">
		<p>Room ID: {{ roomId }}</p>
		<p>Players: {{ players.length }}</p>
		<p>Current player: {{ currentTurnPlayer }}</p>
		<p>Premise: {{ premise }}</p>
	</div>
</template>

<template>
	<div
		class="
			items-start
			max-w-2xl
			border-gray-200
			dark:border-gray-700
			mx-auto
			py-16
		"
	>
		<div class="container mx-auto">
			<!-- <h1
				class="
					font-bold
					text-3xl
					md:text-5xl
					tracking
					mb-2
					text-black
					dark:text-white
					text-center
				"
			>
				Leo 🦁
			</h1> -->

			<p class="text-center text-blue-gray-600 dark:text-blue-gray-300 text-xs">
				{{ hashedText }} 
			</p>

			<div class="py-4">
				<input
					aria-label="Type text"
					type="text"
					placeholder="Type your text here..."
					class="
						mx-auto
						px-4
						py-2
						border border-gray-300
						dark:border-gray-900
						focus:ring-blue-500
						focus:border-blue-500
						block
						max-w-xs
						rounded-md
						bg-white
						dark:bg-gray-800
						text-gray-900
						dark:text-gray-100
					"
					v-model="text"
					@keydown.enter="textToSha256"
				/>
			</div>			
		</div>
	</div>
</template>

<script lang="ts" setup>
const sha256 = async (message) => {
  // encode as UTF-8
  const msgBuffer = new TextEncoder().encode(message)

  // hash the message
  const hashBuffer = await crypto.subtle.digest('SHA-256', msgBuffer)

  // convert ArrayBuffer to Array
  const hashArray = Array.from(new Uint8Array(hashBuffer))

  // convert bytes to hex string
  const hashHex = hashArray.map(b => b.toString(16).padStart(2, '0')).join('')
  return hashHex
}

const text = ref('')
const hashedText = ref('')

const textToSha256 = () => {
	nextTick(async () => {
		hashedText.value = await sha256(text.value)
	})
}
</script>
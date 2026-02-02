<script setup lang="ts">
const props = defineProps({
  highlight: {
    type: String,
    default: 'none',
    validator: (value: string) => {
      return ['culture', 'automation', 'lean', 'measurement', 'share', 'none'].includes(value)
    }
  }
})
</script>

<template>
  <div class="calms-container">
    <div class="ligne1">
      <div class="block automation" :class="{ dimmed: highlight !== 'automation' && highlight !== 'none' }">
        AUTOMATION
      </div>
      <div class="block lean" :class="{ dimmed: highlight !== 'lean' && highlight !== 'none' }">
        LEAN
      </div>
      <div class="block measurement" :class="{ dimmed: highlight !== 'measurement' && highlight !== 'none' }">
        MEASUREMENT
      </div>
      <div class="block share" :class="{ dimmed: highlight !== 'share' && highlight !== 'none' }">
        SHARE
      </div>
    </div>
    <div class="block culture ligne2" :class="{ dimmed: highlight !== 'culture' && highlight !== 'none' }">
      CULTURE
    </div>
  </div>
</template>

<style scoped>
.calms-container {
  display: flex;
  gap: 20px;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.ligne1 {
  display: flex;
  gap: 20px;
  width: 80%;
  height: 300px;
}

.ligne2 {
  width: 80%;
  height: 80px;
}

.block {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: white;
  text-align: center;
  font-size: 20px;
  font-weight: 900;
  border-radius: 10px;
  flex-grow: 1;
}

.culture {
  background-color: green;
}

.automation {
  background-color: #FFB612;
  writing-mode: vertical-rl;
  rotate: 180deg;
}

.lean {
  background-color: #A1006B;
  writing-mode: vertical-rl;
  rotate: 180deg;
}

.measurement {
  background-color: #00A1DE;
  writing-mode: vertical-rl;
  rotate: 180deg;
}

.share {
  background-color: red;
  writing-mode: vertical-rl;
  rotate: 180deg;
}

.dimmed {
  opacity: 0.5;
}
</style>

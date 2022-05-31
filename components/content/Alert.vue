<script setup>
defineProps({
  icon: {
    type: String,
    default: "emojione-monotone:double-exclamation-mark",
  },
});
</script>

<template>
  <div class="p-4 rounded-md bg-emerald-50">
    <div class="flex">
      <div v-if="icon" class="flex-shrink-0 mr-3">
        <Icon
          class="w-5 h-5 text-emerald-700"
          aria-hidden="true"
          :name="icon"
        />
      </div>
      <div>
        <h3 class="m-0 text-base font-medium text-emerald-700">
          <Markdown :use="$slots.title" unwrap="p" />
        </h3>
        <div class="mt-2 text-sm text-emerald-500">
          <Markdown :use="$slots.default" unwrap="p" />
        </div>
      </div>
    </div>
  </div>
</template>

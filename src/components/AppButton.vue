<template>
  <button class="btn primary" @click.prevent="$emit('press')" :disabled="disableButton" type="submit"><slot /></button>
</template>

<script>
export default {
  emits: [ 'press' ],
  props: {
    disableButton: {
      type: Boolean,
      required: false,
      default: false
    }
  }

}

</script>

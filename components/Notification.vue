<template>
  <div class="notification" v-bind:class="notifClass">
    {{ message }}
  </div>
</template>

<script>
export default {
  name: 'Notification',
  props: ['message', 'notifClass']
}
</script>
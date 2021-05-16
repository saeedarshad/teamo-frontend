<template>
  <section class="section">
    <div class="container">
      <h2 class="title">Dashboard</h2>
      <div class="content">
        <p>
          <strong>Name:</strong>
          {{ $auth.user.name }}
        </p>
        <p>
          <strong>Username:</strong>
          {{ $auth.user.username }}
        </p>
        <p>
          <strong>Email:</strong>
          {{ $auth.user.email }}
        </p>
      </div>
    </div>
  </section>
</template>

<script>

export default {
  middleware: 'auth'
}
</script>
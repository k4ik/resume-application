<script>
export default {
  data() {
    return {
      fullname: "",
      email: "",
      phone: "",
      address: "",
    }
  }
}
</script>

<template>
  <main>
    <aside>
      <article>
        <h2>Personal Data</h2>
        <form>
          <label for="name">Full name</label>
          <input type="text" name="name" v-model="fullname">
          <label for="email">E-mail</label>
          <input type="text" name="email" v-model="email">
          <label for="phone">Phone number</label>
          <input type="text" name="phone" v-model="phone">
          <label for="address">Address</label>
          <input type="text" name="address" v-model="address">
        </form>
      </article>
      <article>
        <h2>Experience</h2>
        <form>
          <label>Company</label>
          <input type="text" v-model="company">
          <label>Position title</label>
          <input type="text" v-model="title">
          <label>Start Date</label>
          <input type="text" v-model="sdate">
          <label>End Date</label>
          <input type="text" v-model="edate">
          <label>Description</label>
          <input type="text" v-model="description">
        </form>
        <button>+</button>
      </article>
      <article>

      </article>
    </aside>
    <section>
      <h1>{{fullname}}</h1>
      <p>{{email}}</p>
      <p>{{phone}}</p>
      <p>{{address}}</p>
    </section>
  </main>
</template>

<style scoped></style>

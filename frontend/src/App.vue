<template>
  <main>
    <aside>
      <article>
        <h2>Dados Pessoais</h2>
        <form>
          <label for="fullname">Nome Completo</label>
          <input type="text" name="fullname" v-model="fullname">
          <label for="email">E-mail</label>
          <input type="email" name="email" v-model="email">
          <label for="phone">Número de Telefone</label>
          <input type="tel" name="phone" v-model="phone">
          <label for="address">Endereço</label>
          <input type="text" name="address" v-model="address">
        </form>
      </article>

      <article>
        <h2>Experiência</h2>
        <form v-for="(exp, index) in experiences" :key="index">
          <label for="company">Empresa</label>
          <input type="text" v-model="exp.company">
          <label for="title">Título do Cargo</label>
          <input type="text" v-model="exp.title">
          <label for="sdate">Data de Início</label>
          <input type="date" v-model="exp.sdate">
          <label for="edate">Data de Término</label>
          <input type="date" v-model="exp.edate">
          <label for="description">Descrição</label>
          <textarea v-model="exp.description"></textarea>
        </form>
        <button @click="addExperience">Adicionar Experiência</button>
      </article>

      <article>
        <h2>Educação</h2>
        <form v-for="(edu, index) in educations" :key="index">
          <label for="school">Instituição de Ensino</label>
          <input type="text" v-model="edu.school">
          <label for="degree">Grau Acadêmico</label>
          <input type="text" v-model="edu.degree">
          <label for="sdate">Data de Início</label>
          <input type="date" v-model="edu.sdate">
          <label for="edate">Data de Término</label>
          <input type="date" v-model="edu.edate">
          <label for="description">Descrição</label>
          <textarea v-model="edu.description"></textarea>
        </form>
        <button @click="addEducation">Adicionar Educação</button>
      </article>
    </aside>

    <section>
      <div class="cv-aside"></div>
      <div class="cv-content">
        <h1>{{ fullname }}</h1>
        <div class="data-container" v-if="email">
          <Mail />
          <p>{{ email }}</p>
        </div>
        <div class="data-container" v-if="phone">
          <Phone />
          <p>{{ phone }}</p>
        </div>
        <div class="data-container" v-if="address">
          <MapPin />
          <p>{{ address }}</p>
        </div>
        <h2>Experiência</h2>
        <div v-for="(exp, index) in experiences" :key="index" class="exp-content">
          <h3>{{ exp.company }}</h3>
          <p>{{ exp.title }}</p>
          <p>{{ exp.sdate }} - {{ exp.edate }}</p>
          <p>{{ exp.description }}</p>
        </div>
        <h2>Educação</h2>
        <div v-for="(edu, index) in educations" :key="index"  class="edu-content">
          <h3>{{ edu.school }}</h3>
          <p>{{ edu.degree }}</p>
          <p>{{ edu.sdate }} - {{ edu.edate }}</p>
          <p>{{ edu.description }}</p>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
import { Mail, MapPin, Phone } from 'lucide-vue-next';

export default {
  data() {
    return {
      fullname: "",
      email: "",
      phone: "",
      address: "",
      experiences: [
        {
          company: "",
          title: "",
          sdate: "",
          edate: "",
          description: "",
        },
      ],
      educations: [
        {
          school: "",
          degree: "",
          sdate: "",
          edate: "",
          description: "",
        },
      ],
    };
  },
  methods: {
    addExperience() {
      this.experiences.push({
        company: "",
        title: "",
        sdate: "",
        edate: "",
        description: "",
      });
    },
    addEducation() {
      this.educations.push({
        school: "",
        degree: "",
        sdate: "",
        edate: "",
        description: "",
      });
    },
  },
  components: {
    Mail, MapPin, Phone
  }
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

main {
  display: flex;
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
  font-family: 'Arial', sans-serif;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

aside {
  width: 35%;
  margin-right: 5%;
  padding: 20px;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

article {
  margin-bottom: 20px;
}

h2 {
  font-size: 1.8em;
  color: #333;
  border-bottom: 2px solid #333;
  padding-bottom: 10px;
  margin-bottom: 20px;
}

form {
  display: flex;
  flex-direction: column;
}

label {
  font-weight: bold;
  margin: 10px 0 5px;
}

input[type="text"],
input[type="email"],
input[type="tel"],
input[type="date"],
textarea {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 15px;
  font-size: 1em;
  background-color: #f9f9f9;
}

button {
  background-color: #007bff;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1em;
}

button:hover {
  background-color: #0056b3;
}

section {
  width: 60%;
  display: flex;
  background-color: #fff;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  height: 1200px;
}

.cv-aside {
  width: 100px;
  height: 100%;
  background-color: #007bff;
  border-radius: 8px 0 0 8px;
}

.cv-content {
  padding: 40px 20px;
}

section h1 {
  font-size: 2.5em;
  color: #333;
  margin-bottom: 20px;
}

section .data-container {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
}

section p {
  font-size: 1.2em;
  color: #666;
}

section h2 {
  font-size: 2em;
  color: #333;
  margin-top: 30px;
}

section h3 {
  font-size: 1.5em;
  color: #444;
  margin-bottom: 5px;
}

.exp-content, .edu-content {
  margin-bottom: 20px;
}
</style>

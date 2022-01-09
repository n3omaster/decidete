<template>
  <div>
    <img v-if="img" :src="img" alt="bg" />
    <h1>Decídete asere</h1>

    <div class="bg-dark"></div>

    <div class="decide-container">
      <input
        type="text"
        placeholder="Hazme una pregunta, lo que sea"
        v-model="question"
      />
      <p><small> Recuerda terminar con signo de interrogación [?] </small></p>

      <div v-if="isValidQuestion">
        <h2>{{ question }}</h2>
        <h3>{{ answer == "yes" ? getYes() : getNo() }}</h3>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    async getAnswer() {
      this.answer = "Pérate papi...";
      const { answer, image } = await fetch("https://yesno.wtf/api").then((r) =>
        r.json()
      );
      //console.log({ answer, image });
      this.answer = answer;
      this.img = image;
    },
    async getDoubt() {
      const api = "6SolxKvHKyjFk0n5IQYwnglhEOqYADBn";
      const random = Math.round(Math.random() * 99);
      const { data } = await fetch(
        `https://api.giphy.com/v1/gifs/search?api_key=${api}&limit=1&q=duda&offset=${random}`).then((r) => r.json());
      this.img = data[0].images.original.url;
    },
    getNo() {
      return "Olvídalo";
    },
    getYes() {
      return "Si Papi";
    },
  },
  watch: {
    question(value, oldvalue) {
      //console.log({ value, oldvalue });
      this.isValidQuestion = false;

      if (!value.includes("?")) return;
      this.isValidQuestion = true;

      // Posee un ? so, haz el request HTTP a un backend
      this.getAnswer();
    },
  },
  data() {
    return {
      question: "",
      answer: "Pregunta lo que quieras asere",
      img: this.getDoubt(),
      isValidQuestion: false,
    };
  },
};
</script>

<style scoped>
img,
.bg-dark {
  height: 100vh;
  left: 0px;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
  width: 100vw;
}

.bg-dark {
  background-color: rgba(0, 0, 0, 0.4);
}

.decide-container {
  position: relative;
  z-index: 99;
}

input {
  width: 250px;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;
}
input:focus {
  outline: none;
}

p {
  color: white;
  font-size: 20px;
  margin-top: 0px;
}

h1,
h2 {
  color: white;
}

h2 {
  margin-top: 150px;
}
</style>
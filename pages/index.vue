<template>
  <div class="main-page">
    <header>
      <div class="logo">
        <div class="black-line"></div>
        <div class="red-line"></div>
        <div class="green-line"></div>
      </div>
    </header>
    <div>
      <div class="wrapper-vid">
        <div class="wrapper-img">
          <img alt="" src="/image-top.jpg" loading="lazy" class="image-top">
        </div>
        <form class="form" id="nl" @submit.prevent="sendForm">
          <div class="form-wrapper">
            <h1 class="nl-title">La solution vélo urbain tout-en-un ? C’est GoodBike !</h1>
            <p class="nl-text">Bientôt, un vélo fait pour la ville, bien équipé, maintenance, assurance vol et assistance inclus</p>
            <p class="nl-text">Seulement 22€/mois. Oui, c’est tout.</p>
            <p class="nl-text">Restez connecté-e</p>
            <div class="input-wrapper">
              <input required type="email" placeholder="Ajoutez votre email pour en savoir plus" @input="updateEmail" v-model="email">
            </div>
            <p class="nl-text">Découvrez notre premier modèle et réservez en avant-première.</p>
            <button class="button" type="submit">INSCRIPTION</button>
            <p v-if="success" class="success">{{success}}</p>
            <p v-if="error" class="error">{{error}}</p>
          </div>
        </form>
      </div>
      <div class="page">
        <h2 class="subtitle">EXLPOREZ LA VILLE SANS LIMITES</h2>
        <div class="wrapper-blocks">
          <div class="block-img"><img src="/square_gauche.jpg" alt="" class="image"><p class="text-img">Maintenance mécanique et assistance par téléphone et messagerie incluses</p></div>
          <div class="block-img"><img src="/square_centre.jpg" alt="" class="image"><p class="text-img">Assurance anti-vol incluse</p></div>
          <div class="block-img"><img src="/square_droite.jpg" alt="" class="image"><p class="text-img">Pour seulement 22€ TTC/mois
            sans engagement</p></div>
        </div>
      </div>
      <div>
        <p v-for="data in json_data">{{data.email}}</p>
      </div>
      <div class="wrapper-bottom">
        <div class="wrapper-img-bottom">
          <img src="/bottom.jpg" alt="" class="" class="img-bottom">
        </div>
        <div class="wrapper-text-bottom">
          <h2 class="subtitle-bottom">1000 vélos disponibles le 4 avril 2022 !
          </h2>
          <p class="text-bottom">Il n’y en aura pas pour tout le monde.</p>
          <p class="text-bottom">Rejoignez l’aventure pour découvrir le modèle en avant-première
            et réserver votre GoodBike au printemps prochain.</p>
        </div>
      </div>
      <div class="wrapper-form-bottom">
      <form action="" @submit.prevent="sendForm" class="form-bottom">
        <div class="input-wrapper">
          <input required type="email" placeholder="Ajoutez votre email pour en savoir plus" @input="updateEmail" v-model="email">
        </div>
        <p class="nl-text form-text-bottom">Découvrez notre premier modèle et réservez en avant-première.</p>
        <button class="button" type="submit">INSCRIPTION</button>
        <p v-if="success" class="success">{{success}}</p>
        <p v-if="error" class="error">{{error}}</p>
      </form>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data(){
    return {
      email: '',
      text: '',
      isLoading: false,
      success: null,
      error: null,
      list: [],
      json_data: [
      ],
    }
  },
  methods: {
    updateEmail(value) {
      this.email = value.target.value
    },
    async sendForm(){
      this.success = ''
      this.error = ''
      this.isLoading = true
      await this.$axios
        .post('api/newsletters', { data : {email: this.email, text : this.text}})
        .then(() => {
          this.isLoading = false
          this.email = ''
          this.text = ''
            this.success = 'Votre email a été enregistré'
        })
        .catch(error => {
          this.isLoading = false
          console.log(error)
          this.error = "Une erreur est survenue"
        })

    }
  },
  head () {
    return {
      bodyAttrs: {
        class: 'reset-body'
      }
    }
  }
}
</script>
<style>
.main-page {
  position: relative;
  overflow: hidden;
}
.reset-body, p, h1, h2, h3 {
  padding: 0;
  margin: 0;
  font-family: Avenir;
  font-weight: initial;
}
.video-home {
  width: 100%;
}
.image-top {
  height: 100%;
  width: 100%;
  object-fit: cover;
}
.subtitle {
  text-align: center;
  font-style: italic;
  margin-bottom: 10px;
}
.success {
  color: green;
}
.error {
  color: red;
}
header {
  position: absolute;
  left: 0;
  top: 0;
  z-index: 99;
  display: flex;
  justify-content: space-between;
  padding: 20px;
  padding-right: 40px;
  padding-left: 40px;
  background-color: transparent;
}
.logo {
  width: fit-content;
  transform: rotate(-25deg);
  margin-bottom: 10px;
}
.black-line {
  width: 40px;
  height: 12px;
  background-color: black;
  border-radius: 100px;
}
.red-line {
  width: 60px;
  height: 12px;
  background-color: #FF486D;
  border-radius: 100px;
}
.green-line {
  width: 80px;
  height: 12px;
  background-color: #C8E8E3;
  border-radius: 100px;
}
.page {
  padding: 100px;
  margin: auto;
  max-width: 1380px;
}

.nl-title {
  font-weight: normal;
  font-size: 46px;
  color: white;
  font-weight: bold;
  width: 420px;
  line-height: 50px;
}
.nl-text {
  color: white;
  margin-bottom: 20px;
  max-width: 350px;
  width: 280px;
}
input, textarea {
  border: 1px solid #e1e1e1;
  padding-left: 20px;
  padding-right: 20px;
  padding-top: 5px;
  border-radius: 5px;
  height: 50px;
  width: 100%;
  appearance: none;
}
textarea{
  margin-top: 20px;
  height: 150px;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
input[type='number'] {
  -moz-appearance: textfield;
}
.input::placeholder {
  letter-spacing: 0;
}
.wrapper-vid {
  position: relative;
}
.form {
  background-color: rgba(0,0,0, 0.2);
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  flex-direction: column;
  height: 100%;
  width: 100%;
}
.form-wrapper {
  margin-left: 16%;
  margin-top: 8%;
  width: fit-content;
}
.button {
  font-size: 14px;
  display: flex;
  background-color: #FF486D;
  color: white;
  border-radius: 10px;
  padding-top: 0.3rem;
  padding-left: 3rem;
  padding-right: 3rem;
  width: 250px;
  cursor: pointer;
  text-align: center;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  position: relative;
  min-height: 50px;
  margin-top: 10px;
  border: none;
}
.wrapper-blocks {
  display: flex;
  justify-content: center;
  align-items: center;
}
.block-img {
  width: 33%;
  height: 300px;
}
.image {
  width: 100%;
  object-fit: cover;
  height: 100%;
  position: static;
}
.text-img {
  text-align: center;
}
.block-img:nth-child(2) {
  margin: 20px;
}
.wrapper-bottom {
  padding: 20px;
  display: flex;
  margin-bottom: 50px;
}
.wrapper-img-bottom {
  height: 500px;
  width: 45%;
  margin-right: 20px;
}
.img-bottom {
  width: 100%;
  object-fit: cover;
  height: 100%;
  position: static;
}
.wrapper-text-bottom {
  width: 55%;
  background-color: #C8E8E3;
  display: flex;
  padding: 100px;
  flex-direction: column;
  justify-content: center;
}
.input-wrapper{
  display: flex;
}
.subtitle-bottom {
  font-size: 40px;
  margin-bottom: 20px;
}
.text-bottom {
  font-size: 20px;
}
.wrapper-form-bottom {
  width: fit-content;
  margin: auto;
}
.form-bottom {
  margin-right: 100px;
  margin-left: 100px;
  padding-bottom: 100px;
}
.form-text-bottom {
  color: black;
margin-top: 10px;
}
@media screen and (max-width: 1000px) {
  .nl-title {
    font-size: 32px;
    width: 430px;
  }
  .nl-text {
    margin-top: 10px;
    margin-bottom: 10px;
  }
  .wrapper-text-bottom, .wrapper-img-bottom {
    width: 50%;
  }
  .wrapper-text-bottom {
    padding: 60px;
  }
}
@media screen and (max-width: 800px) {
  .wrapper-bottom {
    flex-direction: column-reverse;
    padding-right: 100px;
    padding-left: 100px;
  }
  .wrapper-text-bottom, .wrapper-img-bottom {
    width: 100%;
  }
  .wrapper-img-bottom {
    height: 280px;
    margin-right: 0;
  }
  .wrapper-text-bottom {
    padding: 40px;
    width: auto;
  }
  .page {
    padding-bottom: 20px;
  }
}
@media screen and (max-width: 900px) {
  .wrapper-blocks {
    flex-direction: column;
  }
  .block-img:nth-child(2){
    margin: initial;
    margin-bottom: 60px;
  }
  .block-img {
    width: 100%;
    margin-bottom: 60px;
  }
}
@media screen and (max-width: 800px) {
  .nl-title {
    position: absolute;
    top: 100px;
    width: 290px;
  }
  .nl-text {
    width: 100%;
    color: black;
  }
  .form-wrapper {
    margin: initial;
    margin-top: 50px;
    width: 100%;
  }
  .form {
    background-color: transparent;
    position: initial;
    padding-right: 100px;
    padding-left: 100px;
    max-width: 1380px;
    width: initial;
  }
  .subtitle {
    font-size: 20px;
  }
  .subtitle-bottom {
    font-size: 26px;
  }
  .text-bottom {
    font-size: 16px;
  }
  .form-bottom {
    margin-right: 20px;
    margin-left: 20px;
  }
}
@media screen and (max-width: 700px) {
  .red-line {
    height: 9px;
    width: 40px;
  }
  .black-line{
    width: 20px;
    height: 9px;
  }
  .green-line {
    width: 60px;
    height: 9px;
  }
  header {
    padding: 10px;
    padding-left: 20px;
    padding-right: 20px;
  }
  .nl-title {
    font-size: 28px;
    line-height: 34px;
    padding: 20px;
    padding-top: 0;
  }
  .form, .page {
    padding-right: 20px;
    padding-left: 20px;
  }
  .page {
    padding-top: 60px;
  }
  .block-img {
    height: 250px;
  }
  .wrapper-bottom {
    flex-direction: column-reverse;
    padding-right: 20px;
    padding-left: 20px;
  }
}
</style>

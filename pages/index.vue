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
      <video poster="https://saikle-prod.fra1.digitaloceanspaces.com/large_video_adb52fcefa.jpg" playsinline="" loop="loop" muted="muted" autoplay="autoplay" class="video-home" data-v-36f5bf99="">
        <source src="/bike_vid.mp4" type="video/mp4" data-v-36f5bf99="">
        <img alt="" src="https://saikle-prod.fra1.digitaloceanspaces.com/large_video_adb52fcefa.jpg" loading="lazy" data-v-36f5bf99="">
      </video>
        <form class="form" id="nl" @submit.prevent="sendForm">
          <h1 class="nl-title">Ce projet vélo vous intéresse ?</h1>
          <p class="nl-text">Inscrivez vous pour être prévenu des actualités et du moment de sa sortie.</p>
          <div class="input-wrapper">
            <input required type="email" placeholder="Ajoutez votre email pour en savoir plus" @input="updateEmail" v-model="email">
          </div>
          <button class="button" type="submit">INSCRIPTION</button>
          <p v-if="success" class="success">{{success}}</p>
          <p v-if="error" class="error">{{error}}</p>
        </form>
      </div>
      <div class="page">
        <h2 class="subtitle">La nouvelle maketplace des vélos d'occasion</h2>
        <div class="wrapper-blocks">
          <div class="block-img"><img src="/image.jpg" alt="" class="image"><p class="text-img">Achetez un super vélo</p></div>
          <div class="block-img"><img src="/image.jpg" alt="" class="image"><p class="text-img">Achetez un super vélo</p></div>
          <div class="block-img"><img src="/image.jpg" alt="" class="image"><p class="text-img">Achetez un super vélo</p></div>
        </div>
      </div>
      <div class="wrapper-bottom">
        <div class="wrapper-img-bottom">
          <img src="/image-bottom.jpg" alt="" class="" class="img-bottom">
        </div>
        <div class="wrapper-text-bottom">
          <h2>Le confort d'un chez-soi, en déplacement
          </h2>
          <p>Pour un voyage d'affaires ou si vous vous installez dans une nouvelle ville, trouvez des logements et des boutiques-hôtels ayant reçu des commentaires 5 étoiles de la part d'autres voyageurs d'affaires.</p>
        </div>
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
      error: null
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
  width: 380px;
  line-height: 50px;
}
.nl-text {
  color: white;
  margin-top: 20px;
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
  margin-left: 16%;
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  flex-direction: column;
  margin-top: 10%;
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
@media screen and (max-width: 1200px) {
  .nl-title {
    width: initial;
  }
}
@media screen and (max-width: 1000px) {
  .nl-title {
    font-size: 32px;
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
  .nl-text {
    color: black;
  }
  .form {
    position: initial;
    padding-right: 100px;
    padding-left: 100px;
    margin: auto;
    margin-top: 50px;
    max-width: 1380px;
  }
  .nl-title {
   position: absolute;
    top: 0;
    margin-top: 15%;
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

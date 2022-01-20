<template>
  <div>
    <header>
      <div class="logo">
        <div class="black-line"></div>
        <div class="red-line"></div>
        <div class="green-line"></div>
      </div>
      <a href="#nl" class="link">Inscription</a>
    </header>
    <div class="page">
      <h1 class="value-proposition">Achetez et Vendez le meilleur du vélo d'occasion</h1>
      <div class="top-section">
        <img class="image" src="https://saikle-prod.fra1.digitaloceanspaces.com/large_CA_2_C3_F5_B_4_B54_4_F42_8212_58_CE_6_C90_AB_66_d37228da6f.jpeg" alt="Vélo d'occasion">
        <div class="top-section-text">
          <h2 class="top-title">Un nouveau projet vélo va voir le jour</h2>
          <p class="top-text">👉 Touvez votre vélo idéal parmis des milliers de vélos d'occasion.</p>
          <p class="top-text">👉 Proposez à la vente votre ancien vélo à des milliers d'acheteurs.</p>
          <p class="top-text">👉 On vous accompagne dans toutes ces étapes.</p>
        </div>
      </div>
      <form class="form" id="nl">
        <h2 class="nl-title">Ce projet vélo vous intéresse ?</h2>
        <p class="nl-text">Incrivez vous pour être prévenu des actualités et du moment de sa sortie.</p>
        <div class="input-wrapper">
          <label for=""></label>
          <input type="text" placeholder="Votre email">
        </div>
        <div class="input-wrapper">
          <label for=""></label>
          <textarea name="" id="" cols="30" rows="10" placeholder="Une question ? Une remarque ? C'est ici..."></textarea>
        </div>
          <button class="button">INSCRIPTION</button>
      </form>
      <div class="label-wrapper">
        <h2 class="label-main-title">Comment acheter un vélo ?</h2>
        <div class="label">
          <h3 class="label-title">Trouvez le vélo qui vous convient</h3>
          <p class="label-emoji">👌</p>
          <p class="label-text">Quelle taille? Quel poid ? Quel modèle ?</p>
          <p class="label-text">On vous aidera à répondre à toutes ces questions de manière simple et intuitive.</p>
        </div>
        <div class="label">
          <h3 class="label-title">Essyez pour être sûr</h3>
          <p class="label-emoji bike">🚲</p>
          <p class="label-text">Vous essayez et vous payez ensuite.</p>
          <p class="label-text">+ 14 jours pour vous rétracter si il y a le moindre soucis.</p>
        </div>
        <div class="label">
          <h3 class="label-title">Des services gratuis</h3>
          <p class="label-emoji">🔧</p>
          <p class="label-text">Une garantie 1an. Un service de réparation.</p>
          <p class="label-text">Une assistance technique en ligne.</p>
          <p class="label-text">Une révision gratuite à 6 mois.</p>
        </div>
      </div>
      <div class="label-wrapper label-wrapper2">
        <h2 class="label-main-title">Comment vendre un vélo ?</h2>
        <div class="label">
          <h3 class="label-title">Publiez en moins de 2 minutes</h3>
          <p class="label-emoji">⏱️</p>
          <p class="label-text">Des conseils à chaque étape pour bien vendre.</p>
          <p class="label-text">Des centaines de milliers de clients disponibles.</p>
        </div>
        <div class="label">
          <h3 class="label-title">Des bonus pour booster votre annonce</h3>
          <p class="label-emoji bike">🚀</p>
          <p class="label-text">La possibilité de faire remonter votre annonce en top liste.</p>
          <p class="label-text">L'occasion de voir votre annonce apparaitre directement dans nos publicités.</p>
        </div>
        <div class="label">
          <h3 class="label-title">Un suivi des ventes utile et intuitif</h3>
          <p class="label-emoji">📊</p>
          <p class="label-text">Un espace de gestion des ventes intuitif.</p>
          <p class="label-text">L'accès à plein de statistiques pour augmenter ses chances de vendre.</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
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
.reset-body, p, h1, h2, h3 {
  padding: 0;
  margin: 0;
  font-family: Avenir;
  font-weight: initial;
}
.top-section {
  display: flex;
  background-color: #fdf474;
  border-radius: 100px;
  padding: 40px;
  margin-bottom: 70px;
}
.top-section-text {
  margin-left: 30px;
  display: flex;
  flex-direction: column;
  font-size: 20px;
}
.top-text {
  margin-bottom: 10px;
}
.top-title {
  margin-bottom: 40px;
  font-size: 30px;
}
.image {
  height: 400px;
  border-radius: 50px;
}
.value-proposition {
  text-align: center;
  font-size: 46px;
  font-weight: bold;
  margin-bottom: 50px;
}
header {
  display: flex;
  justify-content: space-between;
  padding: 20px;
  padding-right: 40px;
  padding-left: 40px;
  border-bottom: 1px solid #e1e1e1;
}
.link {
  margin-top: 10px;
  color: black;
  text-decoration: none;
}
.link:hover {
  opacity: 0.8;
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
.label-wrapper {
  display: flex;
  justify-content: center;
  align-items: baseline;
  position: relative;
  border: 1px solid #FF486D;
  padding: 50px;
  border-radius: 20px;
  text-align: center;
  margin-bottom: 120px;
}
.label-wrapper2 {
  border: 1px solid #C8E8E3;
}
.label-main-title {
  position: absolute;
  top: -30px;
  font-size: 32px;
  background-color: white;
  padding: 10px;
  padding-right: 20px;
  padding-left: 20px;
  left: 50%;
  transform: translateX(-50%);
  border-radius: 5px;
}
.nl-title {
  font-weight: normal;
  font-size: 32px;
  text-align: center;
}
.nl-text {
  margin-top: 20px;
  margin-bottom: 20px;
  max-width: 350px;
  text-align: center;
}
.label{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  max-width: 33%;
}
.label:nth-child(3){
  padding-right: 20px;
  padding-left: 20px;
}
.label:nth-child(2){
  padding-right: 20px;
}
.label:nth-child(4){
  padding-left: 20px;
}
.label-emoji {
  font-size: 40px;
  margin-top: 20px;
  margin-bottom: 20px;
}
.bike {
  font-size: 50px;
}
.label-title {
  font-size: 20px;
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
.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 120px;
}
.input-wrapper {
  width: 50%;
}
.button {
  font-size: 14px;
  display: flex;
  background-color: black;
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
  margin-top: 30px;
  border: none;
}
</style>

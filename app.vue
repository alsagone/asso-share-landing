<template>
  <div id="container">
    <div id="accroche" class="flex col center">
      <span class="titre">Asso Share</span>
      <span class="sous-titre">La solidarité à portée de clic !</span>
    </div>

    <section id="intro" class="flex center">
      Asso Share est une app qui facilite la rencontre entre les associations et
      les bénévoles pour des missions ponctuelles!
    </section>

    <section
      id="credos"
      class="flex col center"
      v-for="credo in listeCredos"
      :key="credo.titre"
    >
      <div class="credo flex col center">
        <span class="credo-titre">{{ credo.titre }}</span>
        <span class="description">{{ credo.description }}</span>
      </div>
    </section>

    <section id="temoignages">
      <span class="titre">Nos utilisateurs témoignent !</span>
      <div class="temoignage-container flex row">
        <div
          class="temoignage flex col"
          v-for="temoignage in temoignages"
          :key="temoignage.prenom"
        >
          <img :src="temoignage.image" alt="" />
          <span class="prenom">{{ temoignage.prenom }}</span>

          <div class="decla">
            <span class="accroche">{{ temoignage.accroche }}</span>
            <span class="texte-temoignage">{{ temoignage.declaration }}</span>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  setup() {
    return {};
  },

  data: () => {
    return {
      listeCredos: [
        {
          titre: "🤝 CONNECTEZ-VOUS À LA SOLIDARITÉ",
          description:
            "Trouvez des missions qui vous passionnent ou des bénévoles enthousiastes pour votre association en un seul endroit.",
        },
        {
          titre: "🌟 MISSIONS QUI COMPTENT",
          description:
            "Que vous cherchiez à donner de votre temps ou à recevoir de l'aide, Asso Share vous met en contact avec les personnes qui partagent vos valeurs.",
        },
        {
          titre: "💼 DES MISSIONS POUR TOUS",
          description:
            "Que vous soyez étudiant, professionnel ou en recherche d’emplois, il y a toujours une mission pour vous. Chacun peut faire la différence !",
        },
      ],

      temoignages: [
        {
          prenom: "Lisa - bénévole",
          image: "https://placehold.co/175x175/8e76ae/fff?text=Hello+World",
          accroche: "Ça n'a jamais été aussi simple d'aider !",
          declaration: "Lorem Ipsum ceci est un témoignage",
        },
        {
          prenom: "Marie - participante",
          image: "https://placehold.co/175x175/8e76ae/fff?text=Hello+World",
          accroche: "Je découvre de nouvelles associations !",
          declaration: "Lorem Ipsum ceci est un témoignage",
        },
        {
          prenom: "Bernard - association",
          image: "https://placehold.co/175x175/8e76ae/fff?text=Hello+World",
          accroche: "Une jolie façon de motiver les gens à agir.",
          declaration: "Lorem Ipsum ceci est un témoignage",
        },
      ],
    };
  },
});
</script>

<style scoped></style>

<style lang="scss">
@import "~/public/styles/style.css";
</style>

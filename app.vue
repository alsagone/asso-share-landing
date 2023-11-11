<template>
  <v-app>
    <div id="container">
      <v-navigation-drawer v-model="sidebar" app>
        <v-list>
          <v-list-tile
            v-for="item in menuItems"
            :key="item.title"
            :to="item.path"
          >
            <v-list-tile-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>{{ item.title }}</v-list-tile-content>
          </v-list-tile>
        </v-list>
      </v-navigation-drawer>

      <v-toolbar app>
        <span class="hidden-sm-and-up">
          <v-toolbar-side-icon @click="sidebar = !sidebar">
          </v-toolbar-side-icon>
        </span>
        <v-toolbar-title> Asso Share </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-xs-only">
          <span v-for="item in menuItems" :key="item.title">
            <a :href="item.path">
              <v-btn flat>
                <v-icon left dark>{{ item.icon }}</v-icon>
                {{ item.title }}
              </v-btn>
            </a>
          </span>
        </v-toolbar-items>
      </v-toolbar>

      <div id="accroche" class="flex col center">
        <span class="titre">Asso Share</span>
        <span class="sous-titre">La solidarité à portée de clic !</span>
      </div>

      <section id="fonctionnement" class="flex center">
        <span class="titre">C'est quoi Asso Share ?</span>

        <div class="flex row">
          <img src="" />
          <p>
            Asso Share est une app qui facilite la rencontre entre les
            associations et les bénévoles pour des missions ponctuelles!
            Plusieurs variations de Lorem Ipsum peuvent être trouvées ici ou là,
            mais la majeure partie d'entre elles a été altérée par l'addition
            d'humour ou de mots aléatoires qui ne ressemblent pas une seconde à
            du texte standard. Si vous voulez utiliser un passage du Lorem
            Ipsum, vous devez être sûr qu'il n'y a rien d'embarrassant caché
            dans le texte.
          </p>
        </div>
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

      <section id="faq"></section>
      <section id="galerie"></section>
    </div>
  </v-app>
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
      sidebar: false,
      menuItems: [
        { title: "Fonctionnement", path: "#fonctionnement", icon: "home" },
        { title: "FAQ", path: "#faq", icon: "face" },
        { title: "Galerie", path: "#galerie", icon: "lock_open" },
      ],
    };
  },
});
</script>

<style scoped></style>

<style lang="scss">
@import "~/styles/style.css";
</style>

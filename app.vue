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
        <v-toolbar-title
          ><img id="logo" src="~/assets/logo.png"
        /></v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-xs-only">
          <span
            class="flex v-center"
            v-for="item in menuItems"
            :key="item.title"
          >
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
        <img id="figures" src="~/assets/figures.jpg" />
      </div>

      <section id="fonctionnement" class="flex col center">
        <span class="titre">LOREM IPSUM !!</span>

        <div class="flex row v-center">
          <p>
            Asso Share est une app qui facilite la rencontre entre les
            associations et les bénévoles pour des missions ponctuelles! Lorem
            ipsum dolor sit amet, consectetur adipiscing elit. Nulla odio ante,
            efficitur ac augue non, tempor vestibulum diam. Sed laoreet justo
            sit amet viverra lacinia. Quisque ultricies iaculis consequat.
            Vivamus aliquam sem sed elit egestas accumsan. In id ex odio. Donec
            sit amet urna sed ligula porttitor sodales placerat eu dui. Praesent
            eu massa sapien. Sed tincidunt lorem a mollis iaculis. In ac urna
            sollicitudin, lobortis lacus sit amet, tincidunt massa. Integer et
            aliquet lorem. Vestibulum dictum congue enim, in tempor orci laoreet
            eget. Donec eleifend quam leo, at dignissim libero ultrices sit
            amet.
          </p>
          <img class="illustration" src="~/assets/don.png" />
        </div>
        <!--
        <div
          class="credo flex col center"
          id="credos"
          v-for="credo in listeCredos"
          :key="credo.titre"
        >
          <span class="credo-titre">{{ credo.titre }}</span>
          <span class="description">{{ credo.description }}</span>
        </div>
        -->
      </section>

      <v-divider />

      <section id="fonctionnement" class="flex col center">
        <span class="titre">C'est quoi Asso Share ?</span>

        <div class="flex row v-center">
          <img class="illustration" src="~/assets/gens.png" />
          <div class="flex col v-center">
            <p>
              Phasellus quam arcu, rutrum nec orci eget, laoreet convallis est.
              Maecenas tempus mollis orci sit amet eleifend. Pellentesque et
              orci mi. Curabitur pellentesque, mi dapibus venenatis consectetur,
              diam turpis viverra velit, et hendrerit orci enim non ipsum.
              Mauris et urna fringilla, suscipit arcu nec, laoreet orci. Quisque
              accumsan dolor id rutrum aliquam. Integer at justo odio. Cras ac
              suscipit erat. Morbi et libero quis nulla tempor posuere.
              Vestibulum mi diam, finibus ac felis eu, laoreet elementum odio.
              Suspendisse sit amet tortor viverra, suscipit diam a, varius
              ligula. Pellentesque placerat ultricies dictum. Curabitur ante
              ipsum, eleifend a orci non, mollis cursus lacus.
            </p>

            <p id="slogan">
              Pour ceux qui veulent aider, fédérer ou juste participer !
            </p>
            <a id="lien-inscription" href="#" ref="noreferrer norelopener"
              ><v-btn
                id="btn-inscription"
                block
                rounded="xl"
                size="x-large"
                color="#8e76ae"
                >Je m'inscris !</v-btn
              ></a
            >
          </div>
        </div>
        <!--
        <div
          class="credo flex col center"
          id="credos"
          v-for="credo in listeCredos"
          :key="credo.titre"
        >
          <span class="credo-titre">{{ credo.titre }}</span>
          <span class="description">{{ credo.description }}</span>
        </div>
        -->
      </section>

      <v-divider />

      <section id="faq" class="flex col center">
        <span class="titre">FAQ</span>
        <v-select
          v-model="reponse"
          :items="faq"
          item-title="question"
          item-value="reponse"
          label="Question"
        ></v-select>

        <p>{{ reponse }}</p>
      </section>

      <v-divider />

      <section id="temoignages" class="flex col center">
        <span class="titre">Nos utilisateurs témoignent !</span>
        <div class="temoignage-container flex row">
          <div
            class="temoignage flex col center"
            v-for="temoignage in temoignages"
            :key="temoignage.prenom"
          >
            <img :src="temoignage.image" class="photo" alt="" />
            <span class="prenom">{{ temoignage.prenom }}</span>

            <div class="decla flex col v-center">
              <span class="accroche">{{ temoignage.accroche }}</span>
              <span class="texte-temoignage">{{ temoignage.declaration }}</span>
              <img class="etoiles" :src="temoignage.imageNote" />
            </div>
          </div>
        </div>
      </section>
      <v-divider />

      <section id="galerie"></section>
    </div>
  </v-app>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Lisa from "~/assets/lisa.png";
import Marie from "~/assets/marie.png";
import Bernard from "~/assets/bernard.png";
import quatreEtoiles from "~/assets/4_etoiles.png";
import cinqEtoiles from "~/assets/5_etoiles.png";

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
          image: Lisa,
          accroche: "Ça n'a jamais été aussi simple d'aider !",
          declaration: "Lorem Ipsum ceci est un témoignage",
          imageNote: quatreEtoiles,
        },
        {
          prenom: "Marie - participante",
          image: Marie,
          accroche: "Je découvre de nouvelles associations !",
          declaration: "Lorem Ipsum ceci est un témoignage",
          imageNote: cinqEtoiles,
        },
        {
          prenom: "Bernard - association",
          image: Bernard,
          accroche: "Une jolie façon de motiver les gens à agir.",
          declaration: "Lorem Ipsum ceci est un témoignage",
          imageNote: quatreEtoiles,
        },
      ],
      sidebar: false,
      menuItems: [
        { title: "Fonctionnement", path: "#fonctionnement", icon: "home" },
        { title: "FAQ", path: "#faq", icon: "face" },
        { title: "Galerie", path: "#galerie", icon: "lock_open" },
      ],
      reponse: "",

      faq: [
        {
          question: "Ceci est la question 1",
          reponse: "Regardez, c'est très simple ! Voici la réponse 1 !",
        },
        {
          question:
            "Oh j'ai une autre question, je peux en poser une deuxième ?",
          reponse: "Bien entendu ! Deux questions ne me font pas peur !",
        },
        {
          question: "Une dernière question pour la route.",
          reponse: "Trois ?! C'est mon nouveau record !",
        },
      ],
    };
  },

  methods: {},
});
</script>

<style scoped></style>

<style lang="scss">
@import "~/styles/style.css";
</style>

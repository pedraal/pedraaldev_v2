<template>
  <div>
    <v-card light class=" mx-6 mx-md-auto mt-4">
      <v-btn
        class="card-btn"
        color="black"
        dark
        small
        absolute
        bottom
        right
        fab
        target="_blank"
        href="https://github.com/pedraal"
      >
        <v-icon>mdi-github</v-icon>
      </v-btn>
      <v-btn
        class="card-btn"
        color="light-blue"
        dark
        small
        absolute
        bottom
        right
        fab
        target="_blank"
        href="https://www.linkedin.com/in/pierre-golfier-9aa804109/"
      >
        <v-icon>mdi-linkedin</v-icon>
      </v-btn>
      <v-btn
        class="card-btn"
        color="indigo"
        dark
        small
        absolute
        bottom
        right
        fab
        href="mailto:pgolfier.pro@gmail.com"
        @click="emailToClipboard"
      >
        <v-icon>mdi-email-send</v-icon>
      </v-btn>
      <v-container>
        <v-row no-gutters justify="center">
          <v-col cols="6" sm="5" md="4" align-self="center">
            <v-img src="/avatar.png" class="mb-4" />
          </v-col>
          <v-col cols="12" md="8" align-self="center" class="pl-4 pr-4">
            <v-row no-gutters align="end">
              <v-col cols="12" sm="7" md="12">
                <h1 class="font-weight-thin">
                  Pierre GOLFIER
                </h1>
                <h2 class="mb-4">
                  Développeur Fullstack
                </h2>
              </v-col>
              <v-col cols="12" sm="5" md="12">
                <p><strong>Age :</strong> {{ age }}</p>
                <p><strong>Lieu :</strong> Haute-Savoie</p>
              </v-col>
            </v-row>

            <p>
              <strong>Freelance :</strong> <v-chip color="error">
                Indisponible
              </v-chip>
            </p>
            <p class="d-block d-sm-flex chip-list">
              <strong class="d-block">Techs :</strong>
              <span>
                <v-chip
                  v-for="tech in techs"
                  :key="tech.name"
                  outlined
                  :color="tech.color"
                  class="mr-1 mb-1"
                >
                  <v-icon>
                    {{ tech.icon }}
                  </v-icon>&nbsp;
                  <span>{{ tech.name }}</span>
                </v-chip>
              </span>
            </p>
            <p class="d-block d-sm-flex chip-list">
              <strong class="d-block">Tools :</strong>
              <span>
                <v-chip
                  v-for="tool in tools"
                  :key="tool.name"
                  outlined
                  :color="tool.color"
                  class="mr-1 mb-1"
                >
                  <v-icon
                    :class="tool.textColor"
                  >
                    {{ tool.icon }}
                  </v-icon>
                  <span
                    :class="tool.textColor"
                  >{{ tool.name }}</span>
                </v-chip>
              </span>
            </p>
          </v-col>
        </v-row>
      </v-container>
    </v-card>
    <v-snackbar
      v-model="snackbar"
      top
      right
    >
      Addresse mail copiée dans le presse-papier
      <template v-slot:action="{ attrs }">
        <v-btn
          color="primary"
          text
          v-bind="attrs"
          @click="snackbar = false"
        >
          Ok
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
export default {
  data () {
    return {
      snackbar: false,
      techs: [
        {
          name: 'VueJs',
          color: 'green',
          icon: 'mdi-vuejs'
        },
        {
          name: 'Nuxt',
          color: 'green',
          icon: 'mdi-nuxt'
        },
        {
          name: 'NodeJs',
          color: 'green darken-3',
          icon: 'mdi-nodejs'
        },
        {
          name: 'MongoDB',
          color: 'green darken-2',
          icon: 'mdi-database'
        },
        {
          name: 'GraphQL',
          color: 'pink',
          icon: 'mdi-graphql'
        },
        {
          name: 'Ruby on Rails',
          color: 'red',
          icon: 'mdi-language-ruby-on-rails'
        },
        {
          name: 'MySQL',
          color: 'blue darken-2',
          icon: 'mdi-database'
        },
        {
          name: 'PostgreSQL',
          color: 'blue darken-2',
          icon: 'mdi-database'
        }

      ],
      tools: [
        {
          name: 'Linux',
          color: 'black',
          icon: 'mdi-linux'
        },
        {
          name: 'Git',
          color: 'orange accent-4',
          icon: 'mdi-git'
        },
        {
          name: 'Vuetify',
          color: 'blue',
          icon: 'mdi-vuetify'
        },
        {
          name: 'Bootstrap',
          color: 'purple lighten-1',
          icon: 'mdi-bootstrap'
        },
        {
          name: 'Netlify',
          color: 'teal accent-4',
          icon: ''
        },
        {
          name: 'Netlify Functions',
          color: 'teal accent-4',
          icon: ''
        },
        {
          name: 'Netlify CMS',
          color: 'teal accent-4',
          icon: ''
        },
        {
          name: 'Cypress',
          color: 'black',
          icon: ''
        },
        {
          name: 'Jest',
          color: 'red darken-4',
          icon: ''
        }
      ]
    }
  },
  computed: {
    age () {
      const birthdate = new Date('1994-04-16')
      const today = new Date()
      return Math.floor((today - birthdate) / 1000 / 60 / 60 / 24 / 365)
    }
  },
  methods: {
    emailToClipboard () {
      const self = this
      navigator.permissions.query({ name: 'clipboard-write' }).then((result) => {
        if (result.state === 'granted' || result.state === 'prompt') {
          navigator.clipboard.writeText('pgolfier.pro@gmail.com').then(function () {
            self.snackbar = true
          }, function () {})
        }
      })
    }
  }
}
</script>

<style lang="scss" scoped>
.v-card {
  max-width: 900px;
}

.card-btn {
  &:nth-of-type(2){
    margin-right: 60px;
  }
  &:nth-of-type(3){
    margin-right: 120px;
  }
}

.chip-list{
  strong {
    min-width: 60px;
  }
}
</style>

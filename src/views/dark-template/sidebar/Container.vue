<template>
  <v-card
    color="grey darken-3"
    dark
  >
    <v-card-text>
      <avatar />
      <div class="text-sm-center mb-4 mt-3">
        <h1>
          Remco <span class="light-blue--text text--lighten-3">Kortekaas</span>
        </h1>
        <span>
          Eigenaar kaaLabs
        </span>
      </div>

      <sidebar-section :options="sections.info" />
      <sidebar-section :options="sections.socials" />
      <sidebar-section :options="sections.hobbies">
        <template v-slot:item="{item}">
          <v-chip>
            <v-avatar>
              <v-icon>
                {{ item.icon }}
              </v-icon>
            </v-avatar>
            {{ item.text }}
          </v-chip>
        </template>
      </sidebar-section>
      <sidebar-section :options="sections.languages">
        <template v-slot:items="{items}">
          <v-container pa-0>
            <v-layout
              wrap
              class="text-xs-center"
            >
              <template
                v-for="(item, i) in items"
              >
                <v-flex
                  :key="i"
                  md3
                  sm4
                  xs6
                >
                  <v-progress-circular
                    rotate="360"
                    size="65"
                    width="2"
                    :value="item.value"
                    color="white"
                    class="ma-2"
                  >
                    {{ item.text }}
                  </v-progress-circular>
                </v-flex>
              </template>
            </v-layout>
          </v-container>
        </template>
      </sidebar-section>
    </v-card-text>
  </v-card>
</template>

<script>
import Avatar from '@/views/dark-template/sidebar/Avatar'
import SidebarSection from '@/views/dark-template/sidebar/Section'
export default {
  name      : 'Sidebar',
  components: { SidebarSection, Avatar },
  data () {
    return {
      sections: {
        info: {
          title: 'INFO',
          items: [
            {
              name: 'Email',
              icon: 'mdi-email',
              text: 'mail@remcokortekaas.nl',
            },
            {
              name: 'Website',
              icon: 'mdi-web',
              text: 'www.remcokortekaas.nl',
            },
            {
              name: 'Birth Date',
              icon: 'mdi-cake-variant',
              text: '21 November 1970',
            },
            {
              name: 'Habitation',
              icon: 'mdi-map-marker',
              text: 'Almere, Nederland',
            },
          ],
        },
        socials: {
          title: 'SOCIALS',
          items: [
            {
              icon: 'mdi-github-circle',
              text: 'github.com/kaalabs',
              link: 'https://github.com/kaalabs',
            },
            {
              icon: 'mdi-linkedin-box',
              text: 'linkedin.com/in/remcokortekaas',
              link: 'https://linkedin.com/in/remcokortekaas',
            },
            {
              icon: 'mdi-twitter',
              text: 'twitter.com/remcokortekaas',
              link: 'https://twitter.com/remcokortekaas',
            },
          ],
        },
        hobbies: {
          title: 'HOBBIES',
          items: [

            {
              icon: 'mdi-bullseye',
              text: 'Getting out of Safe Zone',
            },
            {
              icon: 'mdi-biohazard',
              text: 'Challenges',
            },
            {
              icon: 'mdi-hiking',
              text: 'Hiking',
            },
            {
              icon: 'mdi-image-filter-hdr',
              text: 'Nature',
            },
            {
              icon: 'mdi-account-group',
              text: 'Leadership',
            },
            {
              icon: 'mdi-book-open-page-variant',
              text: 'Reading',
            },
          ],
        },
        languages: {
          title: 'LANGUAGES',
          items: [
            {
              text : 'Dutch',
              value: 100,
            },
            {
              text : 'German',
              value: 50,
            },
            {
              text : 'English',
              value: 70,
            },
          ],
        },
      },
    }
  },
}
</script>

<style scoped>
.sidebar{
    background: #2e2e2e;
}
</style>

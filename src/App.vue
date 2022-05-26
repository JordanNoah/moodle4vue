<template>

  <v-app>
    <v-app-bar app dense elevation="0" clipped-left color="white"
      style="border-bottom: 1px solid rgba(0,0,0,0.1) !important;">
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" :class="!drawer ? 'primary--text': ''"></v-app-bar-nav-icon>
      <v-img src="@/assets/funiber.png" contain max-width="100" max-height="40"></v-img>
      <v-spacer></v-spacer>
      <v-divider vertical inset></v-divider>
      <v-btn icon small class="mx-1">
        <v-icon>
          mdi-bell-outline
        </v-icon>
      </v-btn>
      <v-btn icon small class="mx-1">
        <v-icon>
          mdi-message-outline
        </v-icon>
      </v-btn>
      <span class="mx-2">
        Jhon Doe
      </span>
      <v-avatar color="#e9ecef" size="35">
        JU
      </v-avatar>
      <v-icon>
        mdi-chevron-down
      </v-icon>
    </v-app-bar>
    <v-navigation-drawer :mini-variant.sync="drawer" clipped app>
      <v-list>
        <v-list-item-group active-class="primary--text text--accent-4">
          <v-list-item v-for="item in items" :key="item.title" link>
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
    <v-main>
      <v-container>
        <v-row>
          <v-col>
            <v-card>
              <v-container>
                <v-tabs>
                  <v-tab>My courses</v-tab>
                  <v-tab>Last access</v-tab>
                  <v-tab>Starred courses</v-tab>
                </v-tabs>
                <v-container class="d-flex" style="overflow-x:auto">
                  <v-card height="200" width="300" outlined v-for="n in 10" :key="n" class="mx-1">
                    <v-img src="@/assets/course.jpg" max-height="100" cover class="grey darken-4">
                    </v-img>
                    <div class="d-flex flex-column justify-space-between" style="height:100px;">
                      <div>
                        <div class="text-subtitle-2 mx-3 mt-2">
                          Administracion de bases de datos
                        </div>
                        <div class="mx-3 text-caption">
                          Semestre 5
                        </div>
                      </div>
                      <div class="ma-3">
                        <v-progress-linear value="15"></v-progress-linear>
                        <span class="text-caption">10% complete</span>
                      </div>
                    </div>
                  </v-card>
                </v-container>
              </v-container>
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="3">
            <v-card>
              <v-card-title class="pb-0">
                Calendar events
              </v-card-title>
              <v-container>
                <v-date-picker v-model="date2" :event-color="date => date[9] % 2 ? 'red' : 'yellow'"
                  :events="functionEvents" no-title width="100%"></v-date-picker>
              </v-container>
            </v-card>
          </v-col>
          <v-col cols="3">
            <v-card>
              <v-card-title class="pb-0">
                Timeline
              </v-card-title>
              <v-container>
                <v-list class="py-0">
                  <v-list-item v-for="n in 4" :key="n" link class="pa-0">
                    <v-card width="100%" elevation="0">
                      <v-row no-gutters>
                        <v-col cols="3">
                          <div style="width:100%;height:100%; padding:5px;" class="d-flex align-center">
                            <div
                              style="background-color: #EB66A2; width:100%; padding:7px; border-radius:5px;" class="d-flex align-center">
                              <v-img src="@/assets/assign.svg" style="filter: brightness(0) invert(1);"></v-img>
                            </div>
                          </div>
                        </v-col>
                        <v-col cols="9" class="d-flex flex-column justify-space-between px-2 py-2">
                          <div class="d-flex flex-column">
                            <span class="text-caption text-bold">Assigment</span>
                            <span class="text-caption">Seguridad informatica</span>
                          </div>
                          <span class="text-caption">Tuesday, 24 May 22</span>
                        </v-col>
                      </v-row>
                    </v-card>
                  </v-list-item>
                </v-list>
              </v-container>
            </v-card>
          </v-col>
          <v-col cols="3">
            <v-card>
              <v-card-title class="pb-0">
                Connected
              </v-card-title>
              <v-container>
                <v-list class="py-0">
                  <v-list-item v-for="n in 5" :key="n" link class="pa-0">
                    <v-card width="100%" elevation="0">
                      <v-row no-gutters>
                        <v-col cols="2" class="d-flex justify-center align-center">
                          <v-avatar color="#e9ecef" size="45">
                            JU
                          </v-avatar>
                        </v-col>
                        <v-col cols="10" class="d-flex flex-column justify-space-between px-2 py-2">
                          <div class="d-flex flex-column">
                            <span class="text-subtitle-2">
                              Dani Filip
                            </span>
                            <span class="text-caption">
                              Student
                            </span>
                          </div>
                        </v-col>
                      </v-row>
                    </v-card>
                  </v-list-item>
                </v-list>
              </v-container>
            </v-card>
          </v-col>
          <v-col cols="3">
            <v-card>
              <v-card-title class="pb-0">
                Shared resources
              </v-card-title>
              <v-container>
                <v-card v-for="n in 4" :key="n" class="my-1" elevation="0">
                  <v-container v-if="n%2==0">
                    <v-icon color="red">
                      mdi-file-pdf-box
                    </v-icon>
                    <span>Metro 2033 (PDF) - Dmitry Glukhovsky</span>
                  </v-container>
                  <v-container v-else>
                    <v-icon color="red">
                      mdi-youtube
                    </v-icon>
                    <span>Metro 2033 & Last Light... Years Later</span>
                  </v-container>
                </v-card>
              </v-container>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>

  </v-app>

</template>

<script>
  export default {
    name: 'App',

    data: () => ({
      drawer: true,
      items: [{
          title: 'Dashboard',
          icon: 'mdi-view-dashboard'
        },
        {
          title: 'Courses',
          icon: 'mdi-book'
        },
        {
          title: 'Library',
          icon: 'mdi-bookshelf'
        },
        {
          title: 'Discussions',
          icon: 'mdi-newspaper-variant-multiple-outline'
        },
        {
          title: 'News',
          icon: 'mdi-newspaper'
        },
        {
          title: 'Technical support',
          icon: 'mdi-face-agent'
        },
      ],
      arrayEvents: null,
      date1: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
      date2: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
    }),
    methods: {
      functionEvents (date) {
        const [,, day] = date.split('-')
        if ([12, 17, 28].includes(parseInt(day, 10))) return true
        if ([1, 19, 22].includes(parseInt(day, 10))) return ['red', '#00f']
        return false
      },
    },
  };
</script>
<template>
  <v-container
    :style="$vuetify.breakpoint.xl ? 'padding: 0 15%' : ''"
  >
    <v-row
      class="d-flex flex-column justify-center my-8"
    >
      <h1
        class="mx-auto"
      >
        About Me
      </h1>

      <h4
        class="mx-auto"
      >
        My introduction
      </h4>
    </v-row>

    <v-row>
      <v-col
        md="6"
        sm="12"
        class="d-flex flex-column justify-center align-center"
      >
        <img
          src="@/assets/images/me-profile.png"
          height="300"
          width="230"
        >
      </v-col>

      <v-col
        md="6"
        sm="12"
      >
        <v-row>
          <v-col
            class="text-center"
          >
            <p>mmmmmmmmmmmmmmmmmmmmmm mmmmmmmmmmmmmmmmmmmmmm mmmmmmmmmmmmmmmmmmmmmm mmmmmmmmmmmmmmmmmmmmmm</p>
          </v-col>
        </v-row>

        <v-row>
          <v-col
            md="4"
            sm="4"
            v-for="(experience, i) in experiences"
            :key="i"
          >
            <v-card
              flat
              color="transparent"
            >
              <v-card-title
                class="justify-center"
                style="font-size: 2rem"
              >
                {{ experience.value }}
              </v-card-title>

              <v-card-text
                class="text-center"
              >
                {{ experience.title }}
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>

        <v-row>
          <v-col
            class="d-flex justify-center"
          >
            <v-btn
              dark
              x-large
              elevation="0"
              color="indigo"
              class="mx-auto"
              style="textTransform: none; letter-spacing: 0;"
              download=""
              href="../static/Julián-CV.pdf"
            >
              Download CV

              <img
                src="@/assets/icons/download.svg"
                height="18"
                width="18"
                class="mr-n1 ml-2"
              >
            </v-btn>
          </v-col>
        </v-row>
      </v-col>
    </v-row>

    <v-row
      class="d-flex flex-column justify-center title-wrapper"
    >
      <h1
        class="mx-auto"
      >
        Qualification
      </h1>

      <h4
        class="mx-auto"
      >
        My personal journey
      </h4>
    </v-row>

    <v-row>
      <v-col>
        <v-card
          flat
          color="transparent"
        >
          <v-tabs
            v-model="tab"
            align-with-title
            background-color="transparent"
            color="indigo"
            class="mx-auto"
          >
            <v-tabs-slider
              color="transparent"
            ></v-tabs-slider>

            <v-tab
              v-for="(qualification, i) in qualifications"
              :key="i"
              :class="(i % 2 == 0) ? 'ml-auto' : 'mr-auto'"
            >
              <img
                :src="qualification.icon"
                height="30"
                width="30"
                class="mx-1"
              >
              {{ qualification.title }}
            </v-tab>
          </v-tabs>

          <v-tabs-items
            v-model="tab"
          >
            <v-tab-item
              v-for="(qualification, i) in qualifications"
              :key="i"
            >
              <template>
                <v-timeline
                  align-top
                  class="px-4 py-0 my-4"
                  color="transparent"
                >
                  <v-timeline-item
                    color="indigo"
                    small
                    v-for="(item, j) in qualification.items"
                    :key="j"
                    class="pa-0"
                  >
                    <v-card
                    flat
                    color="transparent"
                    class="ml-auto"
                    >
                      <v-card-title
                        class="pt-0 px-0"
                      >
                        <h2
                          :class="j%2 != 0 ? 'ml-auto' : ''"
                          :style="$vuetify.breakpoint.xs ? 'font-size: 1em' : ''"
                        >
                          {{ item.title }}
                        </h2>
                      </v-card-title>

                      <v-card-text
                        class="d-flex align-center px-0"
                      >
                        <img
                          src="@/assets/icons/location.svg"
                          height="24"
                          width="24"
                          :class="j%2 != 0 ? 'ml-auto mr-2' : 'mr-2'"
                        >

                        {{ item.location }}
                      </v-card-text>

                      <v-card-text
                        class="d-flex align-center py-0 px-0"
                      >
                        <img
                          src="@/assets/icons/date.svg"
                          height="24"
                          width="24"
                          :class="j%2 != 0 ? 'ml-auto mr-2' : 'mr-2'"
                        >

                        {{ item.date }}
                      </v-card-text>
                    </v-card>
                  </v-timeline-item>
                </v-timeline>
              </template>
            </v-tab-item>
          </v-tabs-items>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<style lang="scss" scoped>
.title-wrapper {
  margin-top: 12rem;
  margin-bottom: 3rem;
}

h1 {
  font-size: 3.5rem;
  margin-bottom: 1rem;
}

h4 {
  color: #9E9E9E;
  margin-bottom: 20px;
}
</style>

<script>
export default {
  head() {
    return {
      title: "About"
    }
  },
  data: () => ({
    experiences: [
      {
        title: 'Years experience',
        value: '4+'
      },
      {
        title: 'Projects',
        value: '1'
      },
      {
        title: 'Companies',
        value: '0'
      }
    ],
    qualifications: [
      {
        title: "Education",
        icon: require("@/assets/icons/education.svg"),
        items: [
          {
            title: "Bachiller",
            location: "Madrid - School",
            date: "2014-2017"
          },
          {
            title: "Software Engineer",
            location: "Madrid - University",
            date: "2017-2022"
          }
        ]
      },
      {
        title: "Work",
        icon: require("@/assets/icons/work.svg"),
        items: [
          {
            title: "Incoming...",
            location: "...",
            date: "..."
          }
        ]
      }
    ],
    tab: null,
  })
};
</script>
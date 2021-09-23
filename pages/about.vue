<template>
  <v-container
    :style="$vuetify.breakpoint.xl || $vuetify.breakpoint.sm ? 'padding: 0 15%' : ''"
  >
    <v-row
      class="d-flex flex-column justify-center my-8"
    >
      <h1
        class="mx-auto mb-0"
      >
        About Me
      </h1>

      <p
        class="mx-auto secondary--text"
      >
        My introduction
      </p>
    </v-row>

    <v-row>
      <v-col
        md="6"
        sm="12"
        class="d-flex flex-column justify-center align-center"
      >
        <img
          src="/images/me-profile.png"
          height="300"
          width="230"
        >
      </v-col>

      <v-col
        md="6"
        sm="12"
      >
        <v-row>
          <v-col>
            <p
              class="text-center"
            >
              I am a computer engineering student finishing the last year of my degree. I am passionate about working on professional projects and contributing to digital transformation. I consider myself open, communicative and willing to work as a team.
            </p>
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
                class="text-center secondary--text"
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
              color="primary"
              class="mx-auto"
              href="Julián-CV.pdf"
              download
            >
              Download CV

              <img
                src="/icons/download.svg"
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
      class="mt-16 mb-6 d-flex flex-column justify-center"
    >
      <h1
        class="mx-auto  mb-0"
      >
        Qualification
      </h1>

      <p
        class="mx-auto secondary--text"
      >
        My personal journey
      </p>
    </v-row>

    <v-row>
      <v-col>
        <v-card
          flat
          color="transparent"
        >
          <v-tabs
            centered
            background-color="transparent"
            color="primary"
            v-model="tab"
          >
            <v-tabs-slider
              color="transparent"
            ></v-tabs-slider>

            <v-tab
              background-color="transparent"
              v-for="(qualification, i) in qualifications"
              :key="i"
            >
              <img
                :src="qualification.icon"
                height="30"
                width="30"
                class="mx-1"
                v-if="tab == i"
              >

              <img
                :src="qualification.icon_grey"
                height="30"
                width="30"
                class="mx-1"
                v-else
              >

              {{ qualification.title }}
            </v-tab>
          </v-tabs>

          <v-tabs-items
            v-model="tab"
            style="background-color: transparent"
          >
            <v-tab-item
              v-for="(qualification, i) in qualifications"
              :key="i"
            >
              <v-timeline
                align-top
                class="px-4 py-0 my-12"
              >
                <v-timeline-item
                  small
                  fill-dot
                  color="primary"
                  background-color="transparent"
                  class="pa-0"
                  v-for="(item, j) in qualification.items"
                  :key="j"
                >
                  <v-card
                    flat
                    color="transparent"
                  >
                    <v-card-text
                      :class="j%2 === 0 ? 'pt-0 px-0 pb-1 text-h6' : 'pt-0 px-0 pb-1 text-h6 text-right'"
                    >
                      {{ item.title }}
                    </v-card-text>

                    <v-card-text
                      :class="j%2 === 0 ? 'pt-0 px-0 secondary--text d-flex align-center' : 'pt-0 px-0 secondary--text d-flex align-center justify-end'"
                    >
                      {{ item.location }}
                    </v-card-text>

                    <v-card-text
                      :class="j%2 === 0 ? 'pa-0 secondary--text d-flex align-center' : 'pa-0 secondary--text d-flex align-center justify-end'"
                    >
                      <img
                        src="/icons/date.svg"
                        height="24"
                        width="24"
                        class="mr-2"
                      >

                      {{ item.date }}
                    </v-card-text>
                  </v-card>
                </v-timeline-item>
              </v-timeline>
            </v-tab-item>
          </v-tabs-items>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  head() {
    return {
      title: "About"
    }
  },
  data: () => ({
    tab: 0,
    experiences: [
      {
        title: 'Years experience',
        value: '4+'
      },
      {
        title: 'Projects',
        value: '2'
      },
      {
        title: 'Companies',
        value: '0'
      }
    ],
    qualifications: [
      {
        title: "Education",
        icon: "/icons/education.svg",
        icon_grey: "/icons/education-grey.svg",
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
        icon: "/icons/work.svg",
        icon_grey: "/icons/work-grey.svg",
        items: [
          {
            title: "Incoming...",
            location: "...",
            date: "..."
          }
        ]
      }
    ],
  })
};
</script>
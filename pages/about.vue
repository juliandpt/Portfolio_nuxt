<template>
  <v-container
    :style="$vuetify.breakpoint.xl || $vuetify.breakpoint.sm ? 'padding: 0 15%' : ''"
  >
    <Title
      :title="'About Me'"
      :description="'My introduction'"
    />

    <v-row
      class="margin"
    >
      <v-col
        cols="12"
        md="6"
        class="d-flex justify-center align-center"
      >
        <img
          src="/images/about.png"
          alt="me"
          height="auto"
          width="70%"
          class="rounded"
        >
      </v-col>

      <v-col
        cols="12"
        md="6"
      >
        <v-row>
          <v-col>
            <div
              v-for="(description, i) in descriptions"
              :key="i"
              class="d-flex align-center mb-3"
            >
              <img
                src="/icons/circle-check.svg"
                alt="circle-checkl"
                height="18"
                width="18"
                class="mr-3"
              >

              <span>
                {{ description }}
              </span>
            </div>
            
          </v-col>
        </v-row>

        <v-spacer />

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
                {{ experience.title_top }}

                <br>

                {{ experience.title_bottom }}
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
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
            <v-tab
              background-color="transparent"
              v-for="(qualification, i) in qualifications"
              :key="i"
            >
              <img
                :src="qualification.icon"
                :alt="qualification.title"
                height="30"
                width="30"
                class="mx-1"
                v-if="tab == i"
              >

              <img
                :src="qualification.icon_grey"
                :alt="qualification.title"
                height="30"
                width="30"
                class="mx-1"
                v-else
              >

              <span
                class="mx-1 normalize-text"
                v-if="!$vuetify.breakpoint.xs"
              >
                {{ qualification.title }}
              </span>
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
                :dense="$vuetify.breakpoint.xs"
                class="pt-0 my-12"
              >
                <v-timeline-item
                  small
                  plain
                  color="primary"
                  :right="$vuetify.breakpoint.xs || $vuetify.breakpoint.sm"
                  v-for="(item, j) in qualification.items"
                  :key="j"
                >
                  <v-card
                    flat
                    :outlined="!$vuetify.theme.dark"
                    class="pa-7"
                  >
                    <v-card-text
                      class="text-center text-h5 font-weight-bold"
                      style="padding: 0 0 15px 0;"
                    >
                      {{ item.title }}
                    </v-card-text>

                    <v-card-text
                      class="secondary--text text-center pa-0"
                      v-if="item.company  && item.company.length > 0"
                    >
                      <p class="mb-1">{{ item.company }}</p>
                    </v-card-text>

                    <v-card-text
                      class="secondary--text d-flex align-center justify-center pa-0"
                    >
                      <p class="mb-1">{{ item.date }}</p>
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
    descriptions: [
      "Computer engineer, specialized in web development.",
      "Passionate about working on professional projects.",
      "Open, communicative and willing to work as a team."
    ],
    experiences: [
      {
        title_top: 'Years',
        title_bottom: 'experience',
        value: '1'
      },
      {
        title_top: 'Completed',
        title_bottom: 'projects',
        value: '2'
      },
      {
        title_top: 'Companies',
        title_bottom: 'worked',
        value: '1'
      }
    ],
    qualifications: [
      {
        title: "Education",
        icon: "/icons/education.svg",
        icon_grey: "/icons/education-grey.svg",
        items: [
          {
            title: "Bachelor in Computer Engineering",
            date: "2017 - 2022"
          },
        ]
      },
      {
        title: "Work",
        icon: "/icons/work.svg",
        icon_grey: "/icons/work-grey.svg",
        items: [
          {
            title: "Consulting Intern",
            company: "SAS Institute",
            date: "2021 - present"
          },
        ]
      },
      // {
      //   title: "Courses",
      //   icon: "/icons/courses.svg",
      //   icon_grey: "/icons/courses-grey.svg",
      //   items: [
      //     {
      //       title: "SAS Macro Language 1: Essentials",
      //       location: "SAS",
      //       date: "nov 2021"
      //     },
      //     {
      //       title: "SAS SQL 1: Essentials",
      //       location: "SAS",
      //       date: "nov 2021"
      //     },
      //     {
      //       title: "SAS Certified Specialist: Base Programming Using SAS 9.4",
      //       location: "SAS",
      //       date: "oct 2021"
      //     },
      //     {
      //       title: "SAS Programming 2: Data Manipulation Techniques",
      //       location: "SAS",
      //       date: "oct 2021"
      //     },
      //     {
      //       title: "SAS Programming 1: Essentials",
      //       location: "SAS",
      //       date: "oct 2021"
      //     },
      //     {
      //       title: "Google Cloud Platform Fundamentals: Core Infrastructure",
      //       location: "Coursera",
      //       date: "oct 2020"
      //     },
      //   ]
      // }
    ],
  })
};
</script>
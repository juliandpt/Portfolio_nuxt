<template>
  <v-container
    :style="$vuetify.breakpoint.xl ? 'padding: 0 15%' : ''"
  >
    <v-row
      class="d-flex flex-column justify-center py-8"
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
          src="@/assets/images/profile.jpg"
          height="40"
          width="40"
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
      class="d-flex flex-column justify-center py-8"
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
          width="100%"
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
            >
              {{ qualification.title }}
            </v-tab>
          </v-tabs>

          <v-tabs-items v-model="tab">
            <v-tab-item
              v-for="(qualification, i) in qualifications"
              :key="i"
            >
              <template>
                <v-timeline
                  align-top
                >
                  <v-timeline-item
                    color="indigo"
                    small
                    v-for="(item, j) in qualification.items"
                    :key="j"
                  >
                    <v-card
                      flat
                    >
                      <v-card-title>
                        {{ item.value }}
                      </v-card-title>

                      <v-card-text>
                        {{ item.value }}
                      </v-card-text>

                      <v-card-text
                        class="pt-0"
                      >
                        {{ item.value }}
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
        value: '4'
      },
      {
        title: 'caca',
        value: '4'
      },
      {
        title: 'caca',
        value: '4'
      }
    ],
    qualifications: [
      {
        title: "Education",
        icon: require("@/assets/icons/education.svg"),
        items: [
          {
            value: "caca1",
            location: "",
            years: ""
          },
          {
            value: "caca1",
            location: "",
            years: ""
          },
          {
            value: "caca1",
            location: "",
            years: ""
          }
        ]
      },
      {
        title: "Work",
        icon: require("@/assets/icons/work.svg"),
        items: [
          {
            value: "caca2",
            location: "",
            years: ""
          },
          {
            value: "caca2",
            location: "",
            years: ""
          },
          {
            value: "caca2",
            location: "",
            years: ""
          }
        ]
      }
    ],
    tab: null,
  })
};
</script>
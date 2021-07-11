<template>
  <v-container>
    <v-row>
      <h1
        class="mx-auto"
      >
        My Skills
      </h1>
    </v-row>
      
    <v-row>
      <template
        v-for="(skill, i) in skills"
      >
        <v-col
          cols="12"
          sm="6"
          xs="12"
          class="pb-0"
          :key="i"
        >
          <v-expansion-panels
            flat
          >
            <v-expansion-panel>
              <v-expansion-panel-header>
                {{ skill.title }}
                <template v-slot:actions>
                  <v-icon color="indigo">
                    $expand
                  </v-icon>
                </template>
              </v-expansion-panel-header>

              <v-expansion-panel-content>
                <v-card
                  flat
                  tile
                  v-for="(card, j) in skill.cards"
                  :key="j"
                >
                  <v-card-title
                    class="px-0"
                  >
                    <template
                      class="d-flex"
                    >
                      <p
                        class="ma-0"
                      >
                        {{ card.title }}
                      </p>

                      <p
                        class="ml-auto ma-0"
                      >
                        {{ card.value }}%
                      </p>
                    </template>
                  </v-card-title>

                  <v-card-text
                    class="px-0"
                  >
                    <v-progress-linear
                      rounded
                      color="indigo"
                      :value="card.value"
                    ></v-progress-linear>
                  </v-card-text>
                </v-card>
              </v-expansion-panel-content>
            </v-expansion-panel>
          </v-expansion-panels>
        </v-col>
      </template>
    </v-row>
  </v-container>
</template>

<script>
export default {
  head() {
    return {
      title: "Skills"
    }
  },
  data() {
    return {
      skills: [
        {
          title: "Frontend",
          icon: "@/assests/icons/tags",
          cards: [
            {
              title: "HTML",
              value: 70
            },
            {
              title: "CSS",
              value: 60
            },
            {
              title: "Javascript",
              value: 70
            },
            {
              title: "Angular",
              value: 70
            },
            {
              title: "Vue",
              value: 20
            }
          ]
        },
        {
          title: "Backend",
          icon: "@/assests/icons/server",
          cards: [
            {
              title: "Node",
              value: 70
            },
          ]
        },
        {
          title: "Database",
          icon: "@/assests/icons/tags",
          cards: [
            {
              title: "MariaDB",
              value: 70
            },
            {
              title: "PostgreSQL",
              value: 70
            },
            {
              title: "Firebase",
              value: 60
            }
          ]
        },
        {
          title: "Others",
          icon: "@/assests/icons/tags",
          cards: [
            {
              title: "Python",
              value: 70
            },
            {
              title: "Java",
              value: 70
            },
            {
              title: "C++",
              value: 60
            }
          ]
        },
      ]
    }
  }
};
</script>
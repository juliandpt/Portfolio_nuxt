<template>
  <v-container
    :style="$vuetify.breakpoint.xl ? 'padding: 0 15%' : ''"
  >
    <Title
      :title="'Skills'"
    />
      
    <v-row
      class="margin"
    >
      <v-col
        cols="12"
        sm="6"
        v-for="(skill, i) in skills"
        :key="i"
        :class="$vuetify.breakpoint.xs ? 'pt-0' : ''"
      >
        <v-expansion-panels
          flat
        >
          <v-expansion-panel
            class="transparent"
          >
            <v-expansion-panel-header>
              <div
                class="d-flex align-center"
              >
                <img
                  :src="skill.icon"
                  :alt="skill.title"
                  class="pa-0 mr-3"
                  height="32"
                  width="32"
                >

                {{ skill.title }}
              </div>

              <template
                v-slot:actions
              >
                <v-icon
                  color="primary"
                >
                  $expand
                </v-icon>
              </template>
            </v-expansion-panel-header>

            <v-expansion-panel-content>
              <v-row>
                <v-col
                  cols="6"
                  v-for="(item, i) in skill.items"
                  :key="i"
                >
                  <v-card
                    flat
                    class="d-flex"
                    :color="$vuetify.theme.dark ? '' : 'lighten'"
                  >
                    <div 
                      class="d-flex align-center justify-center"
                    >
                      <img 
                        :src="item.icon"
                        :alt="item.title"
                        class="ml-4"
                        height="25"
                        width="auto"
                      />
                    </div>

                    <v-card-text>
                      {{ item.title }}
                    </v-card-text>
                    
                  </v-card>
                </v-col>
              </v-row>
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
      </v-col>
    </v-row>

    <Title
      :title="'Services'"
    />

    <v-row
      class="margin"
    >
      <v-col
        cols="12"
        md="4"
        sm="6"
        v-for="(service, i) in services"
        :key="i"
        :class="$vuetify.breakpoint.xs ? 'pt-0' : ''"
      >
        <v-card
          loading
          flat
          :color="!$vuetify.theme.dark ? 'lighten' : ''"
          height="100%"
        >
          <template 
            slot="progress"
          >
            <v-progress-linear 
              value="100"
            />
          </template>

          <v-card-title>
            <img 
              :src="service.icon"
              :alt="service.title"
              height="40"
              width="40"
            />
          </v-card-title>
          
          <v-card-title 
            class="pt-0 font-weight-black"
          >
            {{ service.title }}
          </v-card-title>

          <v-divider 
            class="mx-4"
          />

          <v-card-text
            class="px-4 pb-12"
          >
            {{ service.description }}
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>

    <Title
      :title="'Projects'"
    />

    <v-row
      class="margin"
      v-for="(project, i) in projects"
      :key="i"
    >
      <v-col
        :cols="$vuetify.breakpoint.xs ? '12' : '6'"
        :class="$vuetify.breakpoint.xs ? 'text-center' : ''"
        :order="$vuetify.breakpoint.xs ? '2' : i%2 === 0 ? '1' : '2'"
      >
        <h2
          class="my-2 primary--text"
        >
          {{ project.title }}
        </h2>

        <p
          class="my-4"
        >
          {{ project.description }}
        </p>

        <v-btn
          dark
          elevation="0"
          color="primary"
          class="mt-5 mr-auto"
          :href="project.link"
          target="_blank"
          rel="noopener noreferrer"
        >
          See More

          <img
            class="ml-2"
            src="/icons/arrow-white.svg"
            alt="arrow-white"
            height="18"
            width="18"
          >
        </v-btn>
      </v-col>

      <v-col
        :cols="$vuetify.breakpoint.xs ? '12' : '6'"
        :order="$vuetify.breakpoint.xs ? '1' : i%2 === 0 ? '2' : '1'"
        class="shadow d-flex flex-column justify-center align-center"
      >
        <video 
          width='90%'
          muted
          controls
          style="border-radius: 0.35em;"
        >
          <source 
            :src="project.demo" 
            type="video/mp4"
          >

          Your browser does not support the video tag.
        </video>
      </v-col>
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
  data: () => ({
    model: null,
    dialog: false,
    skills: [
      {
        title: "Frontend",
        icon: "/icons/tags.svg",
        items: [
          {
            title: "HTML",
            icon: "/images/html.png"
          },
          {
            title: "CSS",
            icon: "/images/css.png"
          },
          {
            title: "Javascript",
            icon: "/images/javascript.png"
          },
          {
            title: "Typescript",
            icon: "/images/typescript.png"
          },
          {
            title: "Angular",
            icon: "/images/angular.png"
          },
          {
            title: "Vue",
            icon: "/images/vue.png"
          },
          {
            title: "Nuxt",
            icon: "/images/nuxt.png"
          },
          {
            title: "Svelte",
            icon: "/images/svelte.png"
          }
        ]
      },
      {
        title: "Backend",
        icon: "/icons/server.svg",
        items: [
          {
            title: "Node.js",
            icon: "/images/nodejs.png"
          },
          {
            title: "Firebase",
            icon: "/images/firebase.png"
          },
          {
            title: "Flask",
            icon: "/images/flask.png"
          },
        ]
      },
      {
        title: "Database",
        icon: "/icons/database.svg",
        items: [
          {
            title: "MongoDB",
            icon: "/images/mongodb.png"
          },
          {
            title: "PostgreSQL",
            icon: "/images/postgresql.png"
          },
          
        ]
      },
      {
        title: "Others",
        icon: "/icons/brackets.svg",
        items: [
          {
            title: "Python",
            icon: "/images/python.png"
          },
          {
            title: "Java",
            icon: "/images/java.png"
          },
          {
            title: "C++",
            icon: "/images/c++.png"
          }
        ]
      },
    ],
    services: [
      {
        title: "Web development",
        icon: "/icons/layer.svg",
        description: "I perform modern web pages, having knowledge of Multiple frameworks in a Fullstack development."
      },
      {
        title: "UI / UX Design",
        icon: "/icons/ux-design.svg",
        description: "I develope the user interface, design web pages and create ux element interactions."
      },
      {
        title: "Software development",
        icon: "/icons/web-programming.svg",
        description: "I develope quality software products, manage software maintenance, and have Knowledge of some of the most popular programming languages."
      },
      {
        title: "Social skills",
        icon: "/icons/people.svg",
        description: "I am an interactive and communicative person, prefering to work in a team instead of alone."
      },
    ],
    projects: [
      {
        title: "Infopueblo",
        description: "Search webapp of Spanish municipalities. It offers leisure data from the different municipalities, compiling the information through web scrapping.",
        link: "https://github.com/juliandpt/Infopueblo",
        demo: "/videos/infopueblo.mp4"
      },
      {
        title: "Webstats",
        description: "Web service responsible for analyzing the security implemented in the different endpoints of any web domain.",
        link: "https://github.com/juliandpt/Webstats",
        demo: "/videos/webstats.mp4"
      },
    ],
  })
};
</script>
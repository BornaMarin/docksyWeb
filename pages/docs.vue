<template>
  <div class="text-gray-600 body-font">
    <div class="container px-5 py-24 mx-auto w-4/5" v-for="item in data">
      <div class="flex lg:w-3/5 mx-auto border-b pb-4 mb-4 border-gray-200 sm:flex-row flex-col">
        <div class="flex-grow sm:text-left text-left mt-6 sm:mt-0">
          <h2 class="text-gray-900 text-lg title-font font-medium mb-2" :style="`color: ${textColor}`">{{item.title}}</h2>
          <p class="leading-relaxed text-base">{{item.description}}</p>
          <div class="bg-gray-300 rounded-lg pa-2 pl-4 mb-6">
            {{item.path}}
          </div>
          <span >Parameters:</span>
          <v-card class="mt-2" elevation="1">
            <v-simple-table>
              <template v-slot:default>
                <thead>
                <tr>
                  <th class="text-left">
                    Key
                  </th>
                  <th class="text-left">
                    Type
                  </th>
                  <th class="text-left">
                    Required
                  </th>
                </tr>
                </thead>
                <tbody>
                <tr
                  v-for="value in item.values"
                  :key="item.key"
                >
                  <td>{{ value.key }}</td>
                  <td>{{ value.type }}</td>
                  <td>
                    <v-icon
                      v-if="value.required"
                      dark
                      color="green"
                    >
                      mdi-checkbox-marked-circle
                    </v-icon>
                    <v-icon
                      v-else
                    dark
                    color="red"
                  >
                    mdi-cancel
                  </v-icon>

                  </td>
                </tr>
                </tbody>
              </template>
            </v-simple-table>
          </v-card>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
  export default {
    data() {
      return{
        data: [
          {
            title: 'Login route',
            description: 'Path for user login',
            action: 'Post',
            path: '/api/login',
            values: [
              {
                key: 'firstname',
                type: 'string',
                required: true
              },
              {
                key: 'firstname',
                type: 'string',
                required: true
              },
              {
                key: 'firstname',
                type: 'string',
                required: true
              }
            ]
          },
          {
            title: 'Login route',
            description: 'Path for user login',
            action: 'Delete',
            path: '/api/login',
            values: [
              {
                key: 'firstname',
                type: 'string',
                required: false
              }
            ]
          },
          {
            title: 'Login route',
            description: 'Path for user login',
            action: 'Get',
            path: '/api/login',
            values: [
              {
                key: 'firstname',
                type: 'string',
                required: true
              }
            ]
          },
          {
            title: 'Login route',
            description: 'Path for user login',
            action: 'Patch',
            path: '/api/login',
            values: [
              {
                key: 'firstname',
                type: 'string',
                required: true
              }
            ]
          },
          {
            title: 'Login route',
            description: 'Path for user login',
            action: 'Patch',
            path: '/api/login',
            values: [
              {
                key: 'firstname',
                type: 'string',
                required: true
              }
            ]
          }
        ]
      }
    },
    computed: {
        textColor(){
          if(this.$vuetify.theme.dark){
            return 'white'
          }else {
            return 'black'
          }
        }
    }
  }
</script>

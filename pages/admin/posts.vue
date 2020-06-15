<template>
  <div>
    <h1 class="mb-6">Posts</h1>
    <v-btn color="primary" to="/admin/create-post" fab absolute bottom right
      ><v-icon>mdi-plus</v-icon></v-btn
    >
    <client-only>
      <v-data-table
        :headers="headers"
        :items="posts"
        item-key="title"
        class="elevation-1"
        :search="search"
      >
        <template v-slot:top>
          <v-text-field
            v-model="search"
            label="Search"
            class="mx-4"
          ></v-text-field>
        </template>
        <template v-slot:item.actions="{ item }">
          <v-icon small class="mr-2" @click="editContact(item)">
            mdi-pencil
          </v-icon>
          <v-icon small @click="deleteBtn(item)">
            mdi-delete
          </v-icon>
        </template>
      </v-data-table>
    </client-only>
  </div>
</template>

<script>
export default {
  layout: 'admin',
  data() {
    return {
      search: '',
      posts: [
        {
          title: 'Hello World',
          createdAt: new Date().toDateString(),
          updatedAt: new Date().toDateString()
        },
        {
          title: 'Javascript',
          createdAt: new Date().toDateString(),
          updatedAt: new Date().toDateString()
        },
        {
          title: 'Hello World1',
          createdAt: new Date().toDateString(),
          updatedAt: new Date().toDateString()
        }
      ]
    }
  },
  computed: {
    headers() {
      return [
        {
          text: 'Title',
          align: 'start',
          value: 'title'
        },
        {
          text: 'Date Created',
          align: 'Start',
          value: 'createdAt'
        },
        {
          text: 'Date Modified',
          align: 'Start',
          value: 'updatedAt'
        },

        { text: 'Actions', value: 'actions', sortable: false }
      ]
    }
  },
  methods: {}
}
</script>

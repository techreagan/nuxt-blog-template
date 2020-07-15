<template>
  <v-layout>
    <v-flex>
      <v-btn class="mb-10" fab small to="/" color="primary"
        ><v-icon>mdi-chevron-left</v-icon></v-btn
      >
      <h1 class="mb-5">{{ title }}</h1>
      <client-only>
        <div class="output ql-snow">
          <!-- eslint-disable -->
          <div class="ql-editor" v-html="body"></div>
        </div>
      </client-only>
    </v-flex>
  </v-layout>
</template>

<script>
/* eslint-disable */
export default {
  data() {
    return {
      title: '',
      body: ''
    }
  },
  mounted() {
    this.getPost()
  },
  methods: {
    getPost() {
      this.title = 'Welcome to tech reagan blog'
      this.body = this.$htmlDecode(
        `&lt;p>This is about learning JavaScript in three days.&lt;/p>&lt;pre class="ql-syntax" spellcheck="false">const &lt;span class="hljs-type">name&lt;/span> = "Hello world";&lt;span class="hljs-keyword">if&lt;/span>(&lt;span class="hljs-type">name&lt;/span> == "Tech") {alert(&lt;span class="hljs-string">'Tech'&lt;/span>);} &lt;span class="hljs-keyword">else&lt;/span> {alert("I don't know agaan");}&lt;/pre>`
      )
    }
  },
  head() {
    return {
      title: this.title
    }
  }
}
</script>

<template>
  <section class="container">
    <div>
      <textarea :value="input" @input="update"></textarea>
    </div>
    <div v-html="compiledMarkdown"></div>
  </section>
</template>

<script>

import MarkdownIt from 'markdown-it'

const markdownParser = new MarkdownIt({
  html: true,
  linkify: true,
  typographer: true,
})


export default {
  data() {
    return {
      input: "# hello",
    };
  },
  computed: {
    compiledMarkdown: function () {
      return markdownParser.render(this.input);
    }
  },
  methods: {
    update: function (e) {
      this.input = e.target.value;
    }
  }
}

</script>
<style>
.container {
  padding: 4rem;
  display: flex;
  gap: 1rem;


}

textarea {
  width: 100%;
  height: 100%;
  resize: none;
  padding: 1rem;
  box-sizing: border-box;
}

div {
  flex: 1;

}
</style>

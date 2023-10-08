<script>
  import { marked } from "marked";
  let source = `
# H1 heading

## H2 heading

### H3 heading

---

**bold text**

---

*italicized text*

---

> blockquote

---

1. Sahil Dubey
2. Sandesh Patil
3. Shruti Gope

---

- Sahil Dubey
- Sandesh Patil
- Shruti Gope

---

\`code \`

---

[MarkEdit](https://www.markedit.com)

---

![alt text](image.jpg)

---

| Syntax | Description |
| ----------- | ----------- |
| Sahil | Title |
| Sandesh | Text |

---

\`\`\`
{
  "firstName": "Mark",
  "lastName": "Edit",
  "year": 23
}
\`\`\`

---

Here's a sentence with a footnote. [^1]

[^1]: This is the footnote.

---

### MarkEdit {#custom-id}

---

term
: definition

---

~~MarkEdit is bad.~~

---

- [x] Plan & Design
- [ ] Develop & Test
- [ ] Deploy & Review

---


[Svelte](https://svelte.dev/) \\
[Marked](https://marked.js.org/)
`;
  $: markdown = marked(source);
</script>

<main class="container">
  <header class="header">
    <h1 class="header-title">Welcome to MarkEdit!</h1>
  </header>

  <div class="markdown-editor">
    <div class="left-panel">
      <textarea bind:value={source} class="source" />
    </div>

    <div class="right-panel">
      <div class="output">{@html markdown}</div>
    </div>
  </div>
</main>

<style>
  .container {
    background: #262322;
    padding: 10px 30px;
  }
  .header {
    height: 10vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .header-title {
    margin: 0;
    color: #fff;
  }
  .markdown-editor {
    width: 100%;
    display: flex;
    align-items: flex-start;
    justify-content: space-evenly;
  }
  .left-panel,
  .right-panel {
    width: 50%;
    /* border: solid 1px black; */
    border-radius: 2px;
    height: 85vh;
    background: #e5e5e5;
  }
  .right-panel {
    overflow: auto;
  }
  .source {
    border: none;
    width: 100%;
    height: 100%;
    background: #262322;
    color: #e5e5e5;
  }
  .source:focus {
    outline: none;
  }
  .output {
    width: 100%;
    padding: 0 2em;
  }

  ::-webkit-scrollbar-track {
    -webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
    border-radius: 10px;
    background-color: #f5f5f5;
  }

  ::-webkit-scrollbar {
    width: 12px;
    background-color: #f5f5f5;
  }

  ::-webkit-scrollbar-thumb {
    border-radius: 10px;
    -webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
    background-color: #adb5bd;
  }
</style>

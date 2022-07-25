<script>
  import "fluent-svelte/theme.css";
  let count = 0;
  export let creator;
  export let open;
  import { ContentDialog, Button, TextBox, TextBlock } from "fluent-svelte";
  function autoClicker() {
    let counts = setInterval(updated);
    let upto = 0;
    function updated() {
      count = ++upto;
      if (upto === 999) {
        clearInterval(counts);
      }
    }
  }
</script>

<ContentDialog bind:open title="Website made by {creator}">
  Credit: <a href="https://github.com/tropix126/fluent-svelte">Fluent Svelte</a>
  & <a href="https://svelte.dev">svelte</a>
  <svelte:fragment slot="footer">
    <Button on:click={() => (open = false)}>Close</Button>
  </svelte:fragment>
</ContentDialog>

<div class="container">
  <div class="center">
    <div class="textBox">
      <div class="header">
        <TextBlock readonly variant="bodyStrong">1. About me</TextBlock>
        <div>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="16"
            height="16"
            fill="currentColor"
            class="bi bi-credit-card-2-front"
            viewBox="0 0 16 16"
          >
            <path
              d="M14 3a1 1 0 0 1 1 1v8a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V4a1 1 0 0 1 1-1h12zM2 2a2 2 0 0 0-2 2v8a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V4a2 2 0 0 0-2-2H2z"
            />
            <path
              d="M2 5.5a.5.5 0 0 1 .5-.5h2a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-2a.5.5 0 0 1-.5-.5v-1zm0 3a.5.5 0 0 1 .5-.5h5a.5.5 0 0 1 0 1h-5a.5.5 0 0 1-.5-.5zm0 2a.5.5 0 0 1 .5-.5h1a.5.5 0 0 1 0 1h-1a.5.5 0 0 1-.5-.5zm3 0a.5.5 0 0 1 .5-.5h1a.5.5 0 0 1 0 1h-1a.5.5 0 0 1-.5-.5zm3 0a.5.5 0 0 1 .5-.5h1a.5.5 0 0 1 0 1h-1a.5.5 0 0 1-.5-.5zm3 0a.5.5 0 0 1 .5-.5h1a.5.5 0 0 1 0 1h-1a.5.5 0 0 1-.5-.5z"
            />
          </svg>
        </div>
      </div>
      <label for="information">
        <div class="tutorial">
          <br />
          <TextBlock variant="body">Current job</TextBlock>
          <TextBox
            value="Slow down! I am currently studying media technology in Austria."
            readonly
          />
          <br />
          <TextBlock variant="body">Skills</TextBlock>
          <TextBox
            value="Svelte, NodeJS, UI Design, Css, Javascript, Html, Linuxserveradministration, Logo Design, Pixel Art ..some more"
            readonly
          />
          <br />
          <TextBlock variant="body">contact me</TextBlock>
          <TextBox value="Discord: Lսĸas#0001" readonly />
        </div>
      </label>
    </div>

    <div class="textBox centerText">
      <div class="header">
        <TextBlock variant="bodyStrong">2. Counter</TextBlock>
        <div on:click={autoClicker} class="indicator">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="16"
            height="16"
            fill="currentColor"
            class="bi bi-robot"
            viewBox="0 0 16 16"
          >
            <path
              d="M6 12.5a.5.5 0 0 1 .5-.5h3a.5.5 0 0 1 0 1h-3a.5.5 0 0 1-.5-.5ZM3 8.062C3 6.76 4.235 5.765 5.53 5.886a26.58 26.58 0 0 0 4.94 0C11.765 5.765 13 6.76 13 8.062v1.157a.933.933 0 0 1-.765.935c-.845.147-2.34.346-4.235.346-1.895 0-3.39-.2-4.235-.346A.933.933 0 0 1 3 9.219V8.062Zm4.542-.827a.25.25 0 0 0-.217.068l-.92.9a24.767 24.767 0 0 1-1.871-.183.25.25 0 0 0-.068.495c.55.076 1.232.149 2.02.193a.25.25 0 0 0 .189-.071l.754-.736.847 1.71a.25.25 0 0 0 .404.062l.932-.97a25.286 25.286 0 0 0 1.922-.188.25.25 0 0 0-.068-.495c-.538.074-1.207.145-1.98.189a.25.25 0 0 0-.166.076l-.754.785-.842-1.7a.25.25 0 0 0-.182-.135Z"
            />
            <path
              d="M8.5 1.866a1 1 0 1 0-1 0V3h-2A4.5 4.5 0 0 0 1 7.5V8a1 1 0 0 0-1 1v2a1 1 0 0 0 1 1v1a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2v-1a1 1 0 0 0 1-1V9a1 1 0 0 0-1-1v-.5A4.5 4.5 0 0 0 10.5 3h-2V1.866ZM14 7.5V13a1 1 0 0 1-1 1H3a1 1 0 0 1-1-1V7.5A3.5 3.5 0 0 1 5.5 4h5A3.5 3.5 0 0 1 14 7.5Z"
            />
          </svg>
        </div>
      </div>
      <br />
      <TextBlock variant="display">{count}</TextBlock>
      <br />
      <div>
        <Button variant="accent" on:click={() => count++}>Increase Count</Button
        >
        <Button on:click={() => (count = 0)}>Reset Count</Button>
      </div>
      <p>Yes I am just a reactive counter component.</p>
    </div>

    <div class="textBox">
      <div class="header">
        <TextBlock variant="bodyStrong">3. Credits</TextBlock>
        <div class="">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="16"
            height="16"
            fill="currentColor"
            class="bi bi-person-lines-fill"
            viewBox="0 0 16 16"
          >
            <path
              d="M6 8a3 3 0 1 0 0-6 3 3 0 0 0 0 6zm-5 6s-1 0-1-1 1-4 6-4 6 3 6 4-1 1-1 1H1zM11 3.5a.5.5 0 0 1 .5-.5h4a.5.5 0 0 1 0 1h-4a.5.5 0 0 1-.5-.5zm.5 2.5a.5.5 0 0 0 0 1h4a.5.5 0 0 0 0-1h-4zm2 3a.5.5 0 0 0 0 1h2a.5.5 0 0 0 0-1h-2zm0 3a.5.5 0 0 0 0 1h2a.5.5 0 0 0 0-1h-2z"
            />
          </svg>
        </div>
      </div>
      <br />
      <TextBlock variant="body"
        >Check out who was bedhind all of this.<br /><br />Special thanks to all
        my Discord members who support me and give us all great feedback to keep
        improving.</TextBlock
      >
      <br /><br />
      <div>
        <Button variant="accent" on:click={() => (open = true)}
          >Open Creditsmodal</Button
        >
      </div>
    </div>
  </div>
</div>

<style>
  .indicator {
    position: relative;
    top: 0;
    transition: ease 0.5s;
  }

  .indicator:hover {
    transform: scale(1.5);
  }

  .tutorial {
    text-align: left;
  }

  .centerText {
    text-align: center;
  }

  .header {
    display: flex;
    justify-content: space-between;
  }

  .container {
    display: flex;
  }

  .center {
    margin: auto;
    display: flex;
  }

  .textBox {
    background-color: hsl(0deg 0% 13% / 40%);
    max-width: 300px;
    min-width: 250px;
    margin: 10px;
    padding: 1em;
    margin-bottom: 10px;
    border-style: outset;
    border-radius: 10px;
    border-width: 10px;
    border-left: 1px solid rgb(56, 56, 56);
    border-right: 1px solid rgb(56, 56, 56);
    border-top: 1px solid rgb(56, 56, 56);
    border-bottom: 1px solid rgb(56, 56, 56);

    position: relative;
    top: 0;
    transition: top ease 0.5s;
  }

  .textBox:hover {
    top: -10px;
  }

  a {
    color: rgb(104, 204, 252);
    text-decoration: none;
  }

  @media screen and (max-width: 950px) {
    .center {
      flex-direction: column;
    }

    .textBox {
      max-width: none;
      min-width: none;
      width: 20em;
    }
  }

  @media screen and (max-width: 400px) {
    .textBox {
      margin: 0;
      margin-bottom: 10px;
      max-width: none;
      min-width: none;
      width: 10em;
    }
  }
</style>

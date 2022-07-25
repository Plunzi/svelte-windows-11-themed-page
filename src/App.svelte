<script>
  import Content from "./Content.svelte";
  import Header from "./Header.svelte";
  import "fluent-svelte/theme.css";
  import { TextBlock, TextBox } from "fluent-svelte";

  let firstName = "Visitor";
  let lastName = "";
  let color = "#68cdfc";
  let open = false;

  $: fullName = `${firstName} ${lastName}`;
</script>

<Header {firstName} {color} />
<Content creator="Plunzi" {open} />

<main>
  <p style="color: {color};">
    <i>let fullname = " </i>
    {fullName}<i>"; - let color = " </i>{color}<i> ";</i>
  </p>
  <!-- <input type="text" on:input={handleInput} value="{color}">-->
  <label for="selector">
    <div class="container">
      <div class="flex">
        <div class="left">
          <TextBlock variant="body">firstName</TextBlock>
          <TextBox bind:value={firstName} placeholder="Enter any firstname"/>
        </div>
        <div class="left">
          <TextBlock variant="body">lastname</TextBlock>
          <TextBox bind:value={lastName} placeholder="Enter any lastname"/>
        </div>
        <div class="left">
          <TextBlock variant="body">textColor</TextBlock>
          <TextBox bind:value={color} placeholder="Enter a textcolor" />
        </div>
      </div>
    </div>
  </label>
</main>

<style>
  .flex {
    max-width: 860px;
    display: flex;
    margin: auto;
    background-color: hsl(0deg 0% 13% / 40%);
    padding: 1em;
    margin-bottom: 10px;
    border-style: outset;
    border-radius: 10px;
    border-width: 10px;
    border-left: 1px solid rgb(56, 56, 56);
    border-right: 1px solid rgb(56, 56, 56);
    border-top: 1px solid rgb(56, 56, 56);
    border-bottom: 1px solid rgb(56, 56, 56);
  }

  .left {
    min-width: 100px;
    width: 100%;
    max-width: 300px;
    margin: auto;
    text-align: left;
    margin-left: 10px;
    margin-right: 10px;
  }

  i {
    color: rgb(99, 99, 99);
  }

  p {
    color: rgb(64, 63, 63);
  }

  main {
    text-align: center;
    max-width: 240px;
    margin: auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }

  :global(button) {
    margin: initial;
  }

  :global(body) {
    background-color: var(--fds-solid-background-base);
    color: var(--fds-text-primary);
    font-family: var(--fds-font-family-text);
  }

  @media screen and (max-width: 950px) {
    .flex {
      flex-direction: column;
      width: 320px;
    }

    .container {
      margin: auto;
    }
  }

  @media screen and (max-width: 640px) {
    .container {
      position: absolute;
      left: 0;
      right: 0;
    }
  }

  @media screen and (max-width: 350px) {
    .container {
      margin-bottom: 20px;
    }

    .flex {
      width: 93%;
      padding: 10px;
    }

    .left {
      width: 90%;
    }
  }
</style>

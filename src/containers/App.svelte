<script>
  import { onMount } from "svelte";
  import Header from "../components/Header.svelte";
  import Main from "../components/Main.svelte";
  import TimeLine from "../components/TimeLine.svelte";
  import SideBar from "../components/SideBar.svelte";

  let data = {};
  let API = "https://us-central1-pugstagram-co.cloudfunctions.net/data";
  onMount(async () => {
    const response = await fetch(API);
    data = await response.json();
  });
</script>

<style>
  :global(body) {
    background-color: #fafafa;
    color: rgba(38, 38, 38, 0.7);
    font-family: "Times New Roman", Times, serif;
    margin: 0;
    padding: 0;
  }

  :global(h1, h2, h3) {
    margin: 0;
    padding: 0;
  }
</style>

<Header />
<Main>
  <TimeLine posts={data.posts} />
  <SideBar {...data.user} />
</Main>

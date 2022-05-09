<script context="module">
  // @ts-ignore
  export async function load({ fetch, params }) {
    await new Promise(resolve => setTimeout(resolve, 1000)) // wait for 1 second

    const id = params.id // this id is from the filename not from page params!!!
    const res = await fetch(`https://jsonplaceholder.typicode.com/posts/${id}`)
    const guide = await res.json()
    if (res.ok) {
      return {
        props: {
          guide: guide
        }
      }
    } else {
      return {status: 301, redirect: '/guides'}
    } 
  }
</script>

<script>
  export let guide
</script>


<div class="guide">
  <h2>{guide.title}</h2>
  <p>{guide.body}</p>
</div>

<style>
  .guide {
    margin-top: 40px;
    margin: 10px;
    border: 1px dotted rgba(255, 255, 255, 0.2);
  }
</style>
<!-- src/App.svelte -->
<script>
  import Form from './Form.svelte';
</script>

<main>
  <h1>Hello</h1>
  <Form />
</main>

<style>
  main {
    padding: 87px 20px;
    font-family: Arial, sans-serif;
    background: url('./images/bg.png') no-repeat center top / cover;
    width: 100%;
  }

  h1 {
    color: rgb(255, 255, 255);
    font-size: 55px;
    font-weight: 500;
    line-height: 120%;
    letter-spacing: 0%;
    text-align: center;
  }
  @media(max-width:600px){
    h1{
      font-size: 40px;
    }
  }
</style>

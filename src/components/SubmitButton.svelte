<!-- src/components/SubmitButton.svelte -->
<script>
    // export let color = "#007bff";
  </script>
  
  <button type="submit" >Send</button>
  
  <style>
    button {
        border-radius: 50px;
        background: rgb(44, 47, 71);
        border: none;
        cursor: pointer;
        transition: background-color 0.3s;
        color: rgba(255, 255, 255, 0.7);
        font-size: 18px;
        font-weight: 400;
        line-height: 120%;
        padding: 10px 40px;
        margin: 0 auto;
        margin-top: 30px;
    }
  
    button:hover {
      background-color: grey;
    }
  </style>
  
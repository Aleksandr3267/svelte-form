<!-- src/components/SubmitButton.svelte -->
<script>
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
    button:active, button:focus {
      outline: none !important;
    }
    button:hover {
      background-color: rgb(64, 68, 99);
    }
  </style>
  
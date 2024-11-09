<script>
    export let checked = false;
    export let label = "";
    export let error = "";
  </script>
  
  <div class="checkbox">
    <label>
      <input type="checkbox" bind:checked={checked} />
      <span class="checkbox-custom"></span>
      {label}<p>I accept<span>&nbsp;Terms and Privacy Policy</span></p>
    </label>
    {#if error}
      <span class="error-message">{error}</span>
    {/if}
  </div>
  
  <style>
    .checkbox {
      display: flex;
      align-items: center;
      margin-top: 30px;
    }
  
    input {
      display: none; 
    }
  
    .checkbox-custom {
      width: 30px;
      height: 30px;
      border-radius: 8px;
      border: 2px solid rgb(44, 47, 71);
      display: inline-block;
      margin-right: 10px;
      position: relative;
      transition: background-color 0.3s, border-color 0.3s;
    }
  
    input:checked + .checkbox-custom {
      background-color: rgb(44, 47, 71); 
      border-color: rgb(44, 47, 71); 
    }
  
    input:checked + .checkbox-custom::after {
      content: url('./images/arrow.svg');
      color: white; 
      font-size: 16px;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
  
    .error-message {
      color: #d9534f;
      font-size: 0.875rem;
      margin-left: 0.5rem;
    }
    
    .checkbox p{
        text-align: left;
    }
    .checkbox label {
      color: rgb(121, 126, 163);
      font-size: 15px;
      font-weight: 300;
      line-height: 120%;
      display: flex;
      align-items: center;
      margin: 0 auto;
      
    }
    
    .checkbox span:last-child {
      color: rgb(185, 190, 230);
      text-decoration: underline;
    }

    @media(max-width:600px){
        .checkbox label{
            font-size: 12px;
        }
        .checkbox-custom{
            width: 25px;
            height: 25px;
        }
        input:checked + .checkbox-custom::after{
            font-size: 14px;
        }
    }
  </style>
  
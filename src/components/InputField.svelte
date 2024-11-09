<!-- src/components/InputField.svelte -->
<script>
    export let label = "";
    export let type = "text";
    export let value = "";
    export let required = false;
    export let error = "";
  
    let isFocused = false; 
    const handleInput = (e) => {
      value = e.target.value;
    };
  </script>
  
  <div class="input-field">
    <label class:focused={isFocused}>{label}{required ? ' *' : ''}</label>  
    <input 
      type={type} 
      bind:value 
      on:input={handleInput} 
      required={required} 
      class:error={error} 
      class:focused={isFocused}  
      on:focus={() => isFocused = true}  
      on:blur={() => isFocused = false}  
    />
    {#if error}
      <span class="error-message">{error}</span>
    {/if}
  </div>
  
  <style>
    .input-field {
      display: flex;
      flex-direction: column;
    }
    .input-field:first-child{
        margin-top: 10px;
    }
    .input-field:not(:first-child){
        margin-top: 38px;
    }
  
    label {
      font-weight: bold;
      transition: color 0.3s ease;  
      text-align: start;
      color: rgb(121, 126, 163);
      font-size: 15px;
      font-weight: 300;
      line-height: 120%;
      letter-spacing: 0%;

    }
  
    label.focused {
      color: white; 
    }
  
    input {
      padding: 6px 1px;
      border-radius: 0;
      outline: none;
      border: none;
      border-bottom: 1px solid rgb(63, 67, 99);
      background-color: transparent;
      transition: border-color 0.3s ease; 

        color: rgb(255, 255, 255);
        font-size: 18px;
        font-weight: 400;
        line-height: 120%;
    }
  
    input.focused {
      border-color: rgb(255, 255, 255);  
    }
    input.focused.error {
      border-color: #d9534f;  
    }
  
    input:focus + label {
      color: red;  
    }
  
    .error-message {
      color: #d9534f;
      font-size: 0.875rem;
    }
  
    input.error {
      border-color: #d9534f;
    }

    @media(max-width:600px){
      input{
        font-size: 16px;
      }
    }
  </style>
  
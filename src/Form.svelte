<!-- src/Form.svelte -->
<script>
    import InputField from './components/InputField.svelte';
    import Checkbox from './components/Checkbox.svelte';
    import SubmitButton from './components/SubmitButton.svelte';
  
    let formData = {
      name: "",
      company: "",
      email: "",
      phone: "",
      subject: "",
      message: "",
      consent: false
    };
  
    let errors = {};
    let submissionSuccess = false;
  
    function validate() {
        errors = {};
        if (!formData.name) errors.name = "Name is required";
        if (!formData.company) errors.company = "Company is required";
        if (!formData.email) errors.email = "E-mail is required";
        if (!formData.message) errors.message = "Message is required";
        if (!formData.consent) errors.consent = "You must agree to terms";

        // Валидация телефона (например, только цифры и длина от 10 до 15 символов)
        const phonePattern = /^[0-9]{10,15}$/; 
        if (formData.phone && !phonePattern.test(formData.phone)) {
            errors.phone = "Invalid phone number. Please enter 10-15 digits.";
        }

        return Object.keys(errors).length === 0;
    }
  
    function handleSubmit() {
      if (validate()) {
        // Симуляция отправки формы
        submissionSuccess = true;
        setTimeout(() => (submissionSuccess = false), 400000);
      }
    }
  </script>
  
  {#if submissionSuccess}
    <div class="notification">
      Form submitted successfully!
      <button on:click={() => (submissionSuccess = false)}>Close</button>
    </div>
  {/if}
  
  <form on:submit|preventDefault={handleSubmit}>
    <p>For business enquiries please use the form below</p>
    <span>*Required</span>
    <InputField label="Name" bind:value={formData.name} required={true} error={errors.name} />
    <InputField label="Company" bind:value={formData.company} required={true} error={errors.company} />
    <InputField label="E-mail" type="email" bind:value={formData.email} required={true} error={errors.email} />
    <InputField label="Phone" type="tel" bind:value={formData.phone} error={errors.phone} />
    <InputField label="Subject" bind:value={formData.subject} />
    <InputField label="Message" bind:value={formData.message} required={true} error={errors.message} />
    <Checkbox label="" bind:checked={formData.consent} error={errors.consent} />
    <SubmitButton  />
  </form>
  
  <style>
    form {
        max-width: 390px;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        gap: 0;
        background-color: rgb(23, 25, 41);
        padding: 40px 45px;
        border-radius: 27px;
        box-shadow: 0px 0px 50px 0px rgba(0, 0, 0, 0.7);
        margin-top: 27px;
    }
    form p{
        color: rgb(255, 255, 255);
        font-size: 18px;
        font-weight: 400;
        line-height: 120%;
        letter-spacing: 0%;
        text-align: center;
    }
    form span{
        color: rgb(121, 126, 163);
        font-size: 15px;
        font-weight: 300;
        line-height: 120%;
        letter-spacing: 0%;
        text-align: center;
        margin-top: 11px;
    }
    .notification {
      background-color: #d4edda;
      color: #155724;
      padding: 1rem;
      border-radius: 5px;
      margin-bottom: 1rem;
      position: fixed;
      bottom: 20px;
      right: 20px;
      width: fit-content;
    }
  
    .notification button {
      top: 10px;
      right: 10px;
      background: transparent;
      border: none;
      cursor: pointer;
      color: #155724;
    }
    .notification button:active, .notification button:focus {
      outline: none !important;
    }
    @media(max-width:600px){
        form{
            padding: 25px 20px;
        }
        form p{
            font-size: 16px;
        }
        .notification{
            font-size: 11px;
            padding: 5px 10px;
            display: flex;
            align-items: center;
        }
    }
  </style>
  
# svelte multistep form [![NPM Version](https://badge.fury.io/js/svelte-multistep-form.svg?style=flat)](https://npmjs.org/package/svelte-multistep-form)


Multi Step Form help to wrap form elements passing down styles to the component to be rendered, also it presents each form step in a ordered and stylish way.

### Demo
<p align="center">
  <img width="570" src ="./screen/form-demo.gif">
</p>


## Install

```
npm install svelte-multistep-form
```

then import into your code

```javascript
  import { Form, Step } from "svelte-multistep-forms";
```
## Usage

First you need to set up the form `stepsDescription`, `formSubtitle` and `formTitle` inside `multiStepOptions` that later has to be injected into Form component `<Form {multiStepOptions}>`

```javascript
let multiStepOptions = {
    formTitle: "New Title ✍️",
    formSubtitle: "Subtitle should be here",
    stepsDescription: [
      { title: "STEP 1", subtitle: "All the details to perform on this step" },
      { title: "STEP 2", subtitle: "All the details to perform on this step" }
    ]
  };
```

After that you only need to call `Form` and `Step` component in the following way

```html
<Form {multiStepOptions}>
  <Step>
   // Here should be your form
  </Step>
</Form>
```

## Submit form data

```html
<script> 
import axios from "axios";
import { Form, Step } from "svelte-multistep-form";

let multiStepOptions = {
  formTitle: "New Title ✍️",
  formSubtitle: "Subtitle should be here",
  stepsDescription: [
    { title: "Input step", subtitle: "Input to fulfill" },
    { title: "Submit", subtitle: "Save!" },
  ]
};
let myInputValue; 

const handleSubmit = () => {
  const formValues = {
    firstStepInput: myInputValue,
  };
  axios.post('http://my-internal-api/submit', formValues)
  myInputValue = ''
}
</script>

<Form {multiStepOptions}>
  <Step>
   <input
    class="your-custom-class"
    id="form-field"
    bind:value={myInputValue}
    placeholder="value here..." /> 
  </Step>
  <Step>
    <button
      class="your-custom-class"
      on:click|preventDefault={handleSubmit}>
      Save me
    </button>
  </Step>
</Form>
```
> checkout examples folder for demo 

### USING REACT FORM
- To update input fields use `register('input_name', { additional:props })`
- To access props value simply swap register with watch eg `watch("input_name")`
aka subscribe into the input.Use sparingly as it triggers rerenders.
- Validation has been made easier than ever , If any errors are present the onSubmit function is not called. All this is inbuilt.
- Simply gives us just the improved functionality and leaves styling to the dev.
- Leaves us with the freedom to put more custom barriers before the form is submitted
- To validate types eg email.... Just set the input type attribute which will be validated natively by the form before submission. 
- In typescript , zod handles validation better.
- Setting disabled to true leads input value to be undefined and input control to be disabled.`<input {...register("test", {disabled: true})} />`
- Disable externally if you want to keep value.



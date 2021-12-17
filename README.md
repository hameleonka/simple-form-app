# Submit form app
In this app user needs to enter valid name and email in order to submit the form.   
Validation for both input fields is implemented via custom hook useInput:
    `import { useState } from "react";

    const useInput = (validateValue) => {
      const [enteredValue, setEnteredValue] = useState('');
      const [isTouched, setIsTouched] = useState(false);

      const valueIsValid = validateValue(enteredValue);
      const hasError = !valueIsValid && isTouched;

      const inputChangeHandler = (event) => {
        setEnteredValue(event.target.value);
      };
      const inputBlurHandler = (event) => {
        setIsTouched(true);
      };

      const reset = () => {
        setEnteredValue('');
        setIsTouched(false);
      };

      return {
        value: enteredValue,
        isValid: valueIsValid,
        hasError,
        inputChangeHandler,
        inputBlurHandler,
        reset,
      }
    };

    export default useInput;`
 2 validation functions provided for name and email fields.
 Overall form validity is also checked to allow user form submission only if both inputs hold valid values.

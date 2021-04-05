---
layout: post
title:      "Controlled form in React"
date:       2021-04-05 01:00:31 +0000
permalink:  controlled_form_in_react
---


Forms in React are similar to the standard HTML forms in terms of syntax. There are two types of forms in React:  controlled and uncontrolled. In controlled form, we store the data in state, and the form derives its input values from the state. But in uncontrolled form we do not store any data in state. In this article, I am going to explain how we can use controlled form in React.

For each input, we will need a corresponding state to store the input value and a function to handle the input change and update the store accordingly.

I’ll use a simple form to explain it.

```
import { useState } from 'react';

function App() {
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');

  const handleChange = (e) => {
    if (e.target.name === 'name') setName(e.target.value);
    else if (e.target.name === 'email') setEmail(e.target.value);
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log('The name is:', name, 'and the email is :', email);
  };
  return (
    <>
      <h1>React form practice</h1>
      <form onSubmit={handleSubmit}>
        <label>
          Name:
          <input type='text' name='name' value={name} onChange={handleChange} />
        </label>
        <br />
        <label>
          Email:
          <input
            type='text'
            name='email'
            value={email}
            onChange={handleChange}
          />
        </label>
        <br />
        <input type='submit' />
      </form>
    </>
  );
}

export default App;
```

Here we have a functional component that is rendering a form. I have used the ‘useState’ hook to create two state variables: name and email. 
The form has 2 input components. On each input, I am passing on the state variables as the value attribute. So, the name input value will always be the state variable ‘name’, and the email input will be the state variable ‘email.’

We know that the onChange event handler runs on every keystroke. So, I created a function named “handleChange” and set it to the onChange attribute. As a result, whenever a user presses a key, the “handleChange” function will be invoked.

```
const handleChange = (e) => {
    if (e.target.name === 'name') setName(e.target.value);
    else if (e.target.name === 'email') setEmail(e.target.value);
  }
```

If we look at the “handleChange” function, we can see that this function is updating the state variables according to the use input. On the other hand, the value attributes of the input components are set to the state variable. As a result, when a user types something, it is assigned to the state variable, and the value is changed accordingly. So, users see whatever they type in their input boxes.

Now the final step is submitting the form. 

```
  const handleSubmit = (e) => {
    e.preventDefault();
    console.log('The name is:', name, 'and the email is :', email);
  }
```

I have created a function, “handleSubmit,” which prints the state variables when the form is submitted. In a real-world scenario, you’ll make an API call and save the form data.


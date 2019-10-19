# vue-js-form-helper

This is a small library that makes form submit and validation easier to use.

## Installation

```bash
npm i vue-js-form-helper
```

## Code Example

The following code will show how to use it with Vue.js

### html

```html
<div id="app">
    <form @submit.prevent="onSubmit" @keydown="form.errors.clear()">

        <div>
            <input type="text" v-model="form.name" name="name">
            <span v-if="form.errors.has('name')" v-text="form.errors.get('name')"></span>
        </div>

        <div>
            <input type="text" v-model="form.email" name="email">
            <span v-if="form.errors.has('email')" v-text="form.errors.get('email')"></span>
        </div>
        
        <button :disabled="form.errors.any()">Submit</button>
    </form>
</div>
```

### app.js

```js
import axois from 'axios';
import Form from 'vue-js-form-helper';
import vue from 'vue';

<script>

    var app = new Vue({
        el: "#app",
        data: {

            form: new Form({ 
                name: '',
                email: ''
            })

        },
        methods: {
            onSubmit() {

                this.form.submit('post', '/test')
                .then(response => console.log('Success'))
                .catch(error => console.log('Something went wrong'));

            }
        }
    });

</script>
```

## Note

If the name and email field are empty, the error response should be the name and email field with the message.

## Authors and acknowledgment

[Jeffrey Way](https://github.com/laracasts/Vue-Forms) 

## Licence
[MIT License](https://opensource.org/licenses/MIT)
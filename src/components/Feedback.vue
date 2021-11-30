<template>
    <div>
        <div class="container">
        <slot />
        <form>
          <label>Name</label>
          <input
            type="text"
            v-model="name"
            name="name"
            placeholder="Your Name"
          >
          <label>Feedback</label>
          <textarea
            name="message"
            v-model="message"
            cols="30" rows="5"
            placeholder="Message">
          </textarea>
          <div class="row">
              <div class="col">
                  <input type="submit" value="Send">
              </div>
              <div class="col">
                  <input type="submit" value="Send">
                  <Button :btnTitle="cancel" @click="ToggleFeedback"/>
              </div>

          </div>

        </form>
    </div>
    </div>
</template>

<script>
import emailjs from 'emailjs-com';
import Button from './Button.vue';

export default {
  components: { Button },
  name: 'Feedback',
  props: ['Togglefeedback'],

  data() {
    return {
      name: '',
      message: ''
    }
  },
  methods: {
    sendEmail(e) {
      try {
        emailjs.sendForm('slink', 'template_w6gx1t3', e.target,
        'user_TgTPiV6RSsZDfqwRYFpCI', {
          name: this.name,
          message: this.message
        })

      } catch(error) {
          console.log({error})
      }
      // Reset form field
      this.name = ''
      this.message = ''
    },
  }
}
</script>


<style scoped>
* {box-sizing: border-box;}

.container {
  display: block;
  margin:auto;
  text-align: center;
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
  width: 50%;
}

label {
  float: left;
}

input[type=text], [type=email], textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
}

input[type=submit] {
  background-color: #4CAF50;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #45a049;
}
</style>
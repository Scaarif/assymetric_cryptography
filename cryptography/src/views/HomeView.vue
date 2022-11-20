<script setup>

</script>

<template>
  <div class="container">
   <div class="source-message display">
      <!-- input (write the message to encrypt) -->
      <div class="input item">
        <h2>Type a message</h2>
        <!-- <span class="line"></span> -->
        <textarea type="text" v-model="sendersMessage"></textarea>
      </div>
      <!-- include key(senders public key) -->
      <div class="key item">
        <h2>&lt;- sender's key -></h2>
        <span class="line"></span>
        <span>{{ sendersKey }}</span>
      </div>
      <!-- display the message (as original/typed) -->
      <div class="original-text item">
        <h2>your text, let's encrypt it!</h2>
        <span class="line"></span>
        <p>{{ sendersMessage }}</p>
      </div>
   </div>
   <div class="decryption display">
      <!-- display encrypted key (senders public key) -->
      <div class="key">
        <p>&lt;- your key, encrypted (:just coz we can do that:) -></p>
        <span>actual key</span>
      </div>
      <!-- Display encrypted version (of message)? -->
      <div class="original-text">
        <p>There we are! It's all encrypted and safely on transit...</p>
        <span>actual message</span>
      </div>
    </div>
    <div class="received-message display">
      <!-- display decrypted key (senders public key) -->
      <div class="key">
        <p>&lt;- senders key, decrypted -></p>
      </div>
      <!-- Display decrypted version (of message)? -->
      <div class="original-text">
        <p>...And, your message, safely delivered & readable:)</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      sendersMessage: '',
      actualText: '',
      sendersKey: 'hello there!',
    }
  }
}
</script>
<style scoped>
.container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  width: 100%;
}
h2 {
  text-align: center;
  text-transform: capitalize;
  /* color: var(--color-text); */
}
.display {
  /* border: 1px solid var(--color-border); */
  margin-block: 1rem;
  padding: 2rem;
}
.item {
  min-width: 400px;
  border: 1px solid var(--color-border);
  border-radius: 30px;
  padding: 2rem;
}
.item:last-of-type{
  /* border-right: none; */
}

.line:first-of-type {
  display: block;
  border: 1px solid red;
}
.line:last-of-type {
  display: block;
  border: 1px solid orange;
}
.source-message {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  gap: 2rem;
}
.key span:last-of-type {
  display: block;
  padding-top: 1rem;
  /* color: red; */
  text-align: center;
  /* border: 1px solid red; */
}

.source-message textarea {
  background: var(--color-background-soft) ;
  min-height: 80%;
  width: 100%;
  /* border: 1px solid var(--color-border); */
  border: none;
  border-radius: 10px;
  outline: none;
  margin-top: .5rem;

  padding: .5rem;
  color: #f2f2f2;
}

.display div:nth-child(3) p
{
  /* border: 1px solid red; */
  margin-top: 1rem;
  padding-inline: .5rem;
  min-height: 60%;
  border-bottom-right-radius: 15px;
  background: var(--color-background-soft);
}
.decryption {

}

.received-message {
  /* border: 1px solid var(--color-border); */
  /* height: 100px; */
  /* width: 1000px; */
}
</style>

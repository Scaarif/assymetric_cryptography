<script setup>

</script>

<template>
  <div class="container">
    <div class="header">
      <h1>Master Encryption</h1>
    </div>
   <div class="source-message display">
      <!-- input (write the message to encrypt) -->
      <div class="input item">
        <h2>Type a message</h2>
        <!-- <span class="line"></span> -->
        <form @submit.prevent="handleSubmit">
          <textarea type="text" v-model="sendersMessage"></textarea>
          <button>submit</button>
      </form>
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
      <div class="key item">
        <h2>your key, encrypted (:just coz we can do that:)</h2>
        <span class="line"></span>
        <span>{{ sendersKeyEncrypted }}</span>
      </div>
      <!-- Display encrypted version (of message)? -->
      <div class="original-text item">
        <h2>There! message all encrypted and safely on transit...</h2>
        <span class="line"></span>
        <p>{{ encryptedMessage }}</p>
      </div>
    </div>
    <div class="received-message display">
      <!-- display decrypted key (senders public key) -->
      <div class="key item">
        <h2>&lt;- senders key, decrypted -></h2>
        <span class="line"></span>
        <span>{{ decryptedKey }}</span>
      </div>
      <!-- Display decrypted version (of message)? -->
      <div class="original-text item">
        <h2>...And, your message, safely delivered & decrypted:)</h2>
        <span class="line"></span>
        <p>{{ decryptedMessage }}</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      sendersMessage: '',
      sendersKey: 'hello there!',
      sendersKeyEncrypted:'!ereht olleh',
      encryptedMessage:'on transit, safe and sound...',
      decryptedKey:'hello there!',
      decryptedMessage:'well, there you have it!',
    }
  }
}
</script>
<style scoped>
.container {
  max-width: 1280px;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  width: 100%;
  padding-right: 1rem;
}
.header{
  margin-bottom: 1rem;
  margin-top: 0;
  padding-block: 1rem;
  border-block: 1px solid var(--color-background-soft);
  text-align: center;
  text-transform: capitalize;
  color:#f2f2f2;
  letter-spacing: .1rem;
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
  min-width: 380px;
  border: 1px solid var(--color-border);
  border-radius: 30px;
  padding: 2rem;
}

.line:first-of-type {
  display: block;
  border: 1px solid red;
}
.line:last-of-type {
  display: block;
  border: 1px solid orange;
}
.source-message, .decryption, .received-message {
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

.source-message form {
  display: flex;
  flex-direction: column
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

.source-message button {
  margin-top: 1rem;
  background: orange;
  /* color: #f2f2f2; */
  border: none;
  border-radius: 10px;
  padding: .5rem 1rem;
  justify-self: flex-end;
  align-self: flex-end;
} 

.source-message .item:first-of-type {
  padding-bottom: 1rem;
}
.display div:nth-child(3) p,
.source-message div:nth-child(2) span:last-child,
.decryption div:nth-child(2) p,
.decryption div:nth-child(1) span:last-child,
.received-message div:nth-child(2) p,
.received-message div:nth-child(1) span:last-child
{
  /* border: 1px solid red; */
  margin-top: 1rem;
  padding-inline: .5rem;
  min-height: 60%;
  border-bottom-right-radius: 15px;
  background: var(--color-background-soft);
}
.decryption div:nth-child(1) span:last-child,
.received-message div:nth-child(1) span:last-child,
.decryption div:nth-child(2) p
{
  border-bottom-right-radius: 0;

}
.received-message div:nth-child(1) span:last-child,
.source-message div:nth-child(2) span:last-child
{
  border-bottom-left-radius: 15px;
}
.decryption .item,
.received-message .item
{
  min-width: 40%;
}
.decryption .line
{
  border: 1px solid var(--color-text);
}
.decryption .key span:last-child,
.decryption .original-text p {
  color: orange;
}

.received-message .line
{
  border: 1px solid greenyellow;

}
.decryption .item {
  border: none;
}
.decryption .item:first-of-type {
  border-left: 1px solid var(--color-background-soft);
}
.decryption .item:last-of-type {
  border-right: 1px solid var(--color-background-soft);
}
.received-message .item {
  border-top-left-radius: 0;
  border-top-right-radius: 0;
}
.received-message .item:first-of-type {
  border-bottom-right-radius: 0;
}

.received-message .item:last-of-type {
  border-bottom-left-radius: 0;
}

@media screen and (max-width: 1240px) {
  .container {
    padding-right: 0;
  }
  .source-message, .decryption, .received-message {
    flex-wrap: wrap;
    gap: 1rem;
  }
}
@media screen and (max-width: 1070px) {
  .received-message .item:first-of-type {
    /* border-left: none; */
    border-bottom-left-radius: 0;
  }
  .decryption {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .received-message {
    display: flex;
    align-items: center;
    justify-content: flex-end;
  }
}
</style>

<template>
  <form class="container" @submit.prevent="submitRate" v-if="!openThanks">
    <div class="star">
      <iconsStar />
    </div>
    <h2>How did we do?</h2>
    <p>Please let us know how we did with your support request. All feedback is appreciated to help us improve our
      offering!</p>
    <div class="rates">
      <label v-for="i in 5"><input type="radio" :id="i" v-model="userRate" :value="i"> <span>{{ i
      }}</span></label>

    </div>

    <button type="submit">Submit</button>

  </form>


  <div class="container thanks" v-else>
    <iconsThankYou />
    <p class="rateInfo">You selected {{ userRate }} out of 5</p>
    <h2>Thank you!</h2>
    <p>We appreciate you taking the time to give a rating. If you ever need more support, don’t hesitate to get in
      touch!</p>
  </div>
</template>

<script setup>
const userRate = ref(0)
const openThanks = ref(false)
const submitRate = () => {
  openThanks.value = true
}

</script>

<style lang="scss">
.container {
  width: 412px;
  height: 416px;
  background: $dark-gradient;
  border-radius: 30px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: space-around;
  font-family: 'Overpass', sans-serif;



  .star {
    margin-left: 32px;
    margin-top: 32px;
    display: flex;
    justify-content: center;
    align-items: center;
    max-width: 48px;
    max-height: 48px;
    min-width: 40px;
    min-height: 40px;
    background-color: $dark-blue;
    border-radius: 50%;
    width: fit-content;
  }

  h2 {
    padding: 0 32px;
    color: #fff;
    font-weight: bold;
    font-size: 28px;
    margin-bottom: 0;
  }

  p {
    padding: 0 32px;
    color: $light-grey;

  }

  .rates {
    display: flex;
    justify-content: space-evenly;
    width: 100%;

    label {

      border-radius: 50%;
      width: 51px;
      height: 51px;
      transition: 0.5s;
      position: relative;


      input[type="radio"] {
        position: absolute;
        width: 100%;
        height: 100%;
        opacity: 0;
        z-index: 10;
        top: 0;
        left: 0;
        height: 100%;
        width: 100%;
        margin: 0;
        padding: 0;
        border-radius: 50%;
        -webkit-appearance: none;
        -moz-appearance: none;
        cursor: pointer;

        &:hover+span {
          background-color: $light-grey;
          color: #fff;


        }

        &:checked+span {
          background-color: $orange;
          color: #fff;

        }
      }

      span {
        background-color: $dark-blue;
        color: $light-grey;
        border-radius: 50%;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 0;
        transition: 0.2s;
      }

    }

  }

  button {
    width: 90%;
    height: 48px;
    background-color: $orange;
    border-radius: 24px;
    border: none;
    color: #fff;
    font-weight: bold;
    font-size: 15px;
    cursor: pointer;
    transition: 0.5s;
    margin: auto;

    &:hover {
      background-color: #fff;
      color: $orange;

    }
  }
}

.thanks {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;


  .rateInfo {

    color: $orange;
    background-color: $dark-blue;
    padding: 10px 32px;
    border-radius: 24px;

  }
}

@media screen and (max-width: 412px) {
  .container {
    width: 327px;
    height: 360px;

    h2{
      font-size: 24px;
    }

    p{
      font-size: 14px;
    }

    .rates label {
      width: 42px;
      height: 42px;

      span{
        font-size: 14px;
      }

      
    }
  }
}
</style>


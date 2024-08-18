<script>
  import { createEventDispatcher } from 'svelte';

  let dispatch = createEventDispatcher();

  function onClick() {
    dispatch('click', 'button1');
  }

  export let btnClass;
  export let btnLabel;
</script>

<button class="btn {btnClass}" on:click>{btnLabel}</button>

<style lang="scss">
  @use '../scss/vars';

  .btn {
    position: absolute;
    font-size: 1.1rem;
    text-transform: uppercase;
    padding: 0.2rem;
    width: 7rem;
    color: #444;
    background: none;
    border: none;
    font-family: inherit;
    cursor: pointer;
    font-weight: 400;
    transition: all 0.2s;
    background-color: #fff;
    background-color: rgba(255, 255, 255, 0.6);
    backdrop-filter: blur(10px);
    border-radius: 20px;
    box-shadow: 0 1.75rem 3.5rem rgba(0, 0, 0, 0.1);
    @media screen and (min-width: vars.$sm) {
      width: auto;
      padding: 1rem;
    }
    &::first-letter {
      font-size: 1.9rem;
      display: inline-block;
    }
    &:active {
      transform: translate(-2%, -47%);
      box-shadow: 0 1rem 2rem rgba(0, 0, 0, 0.15);
    }
    &:focus {
      outline: none;
      @media screen and (min-width: vars.$sm) {
        &:active {
          transform: translate(-50%, 3px);
          box-shadow: 0 1rem 2rem rgba(0, 0, 0, 0.15);
        }

        @media screen and (min-width: vars.$lg) {
          font-size: 1.8rem;
        }
      }
    }
  }
  .btn--new {
    top: 46%;
    left: 0;
    transform: translateY(-50%);
    @media screen and (min-width: vars.$sm) {
      top: 1rem;
      transform: translate(-50%);
      left: 50%;
    }
    @media screen and (min-width: vars.$lg) {
      top: 4rem;
      transform: translate(-50%);
      left: 50%;
    }
  }

  .btn--roll {
    top: 46%;
    right: 0;
    transform: translateY(-50%);
    @media screen and (min-width: vars.$sm) {
      transform: translate(-50%);
      top: 33rem;
      left: 50%;
      max-width: 15rem;
      font-size: 1.6rem;
      padding: 1rem 0.6rem;
    }
    @media screen and (min-width: vars.$lg) {
      transform: translate(-50%);
      max-width: auto;
      top: 32rem;
      left: 50%;
      font-size: 1.8rem;
    }
  }

  .btn--hold {
    bottom: 34%;
    right: 0;
    height: 4rem;
    // &:active {
    //   transform: translate(-2%, 5%);
    // }
    @media screen and (min-width: vars.$sm) {
      top: 38rem;
      bottom: auto;
      max-width: 15rem;
      left: 50%;
      height: auto;
      transform: translate(-50%, 3px);
    }
  }
</style>

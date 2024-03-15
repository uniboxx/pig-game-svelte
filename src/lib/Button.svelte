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

<style lang="stylus">
  @import '../../public/styl/_variables.styl'
  
  .btn
    position absolute
    font-size 1.2rem
    text-transform uppercase
    padding 0.3rem .2rem
    width 6rem
    &::first-letter
        font-size 1.8rem
        display inline-block
    &:active
      transform translate(-50%, 3px)
      box-shadow 0 1rem 2rem rgba(0, 0, 0, 0.15)
    &:focus
      outline none
    @media screen and (min-width sm)
      width auto
      left 50%
      transform translate(-50%)
      color #444
      background none
      border none
      font-family inherit
      font-size 1.8rem
      cursor pointer
      font-weight 400
      transition all 0.2s
      background-color white
      background-color rgba(255, 255, 255, 0.6)
      backdrop-filter blur(10px)
      padding 0.7rem 2.5rem
      border-radius 50rem
      box-shadow 0 1.75rem 3.5rem rgba(0, 0, 0, 0.1)
      &::first-letter
        font-size 2.4rem
        display inline-block
        margin-right 0.7rem
      &:active
        transform translate(-50%, 3px)
        box-shadow 0 1rem 2rem rgba(0, 0, 0, 0.15)
      &:focus
        outline none
  .btn--new
    top 50%
    transform translateY(-50%)
    @media screen and (min-width sm)     
      top 4rem
      transform translate(-50%)
      left 50%

  .btn--roll
    top 50%
    right 0
    transform translateY(-50%)
    @media screen and (min-width sm)
      transform translate(-50%)
      top 39.3rem
      left 50%

  .btn--hold
    bottom 0
    right 0
    @media screen and (min-width sm)
      top 46.1rem
      bottom auto
      left 50%
</style>

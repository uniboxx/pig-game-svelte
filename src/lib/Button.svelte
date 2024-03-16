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
    font-size 1.1rem
    text-transform uppercase
    padding 0.2rem
    width 7rem
    color #444
    background none
    border none
    font-family inherit
    cursor pointer
    font-weight 400
    transition all 0.2s
    background-color white
    background-color rgba(255, 255, 255, 0.6)
    backdrop-filter blur(10px)
    border-radius 20px
    box-shadow 0 1.75rem 3.5rem rgba(0, 0, 0, 0.1)
    &::first-letter
        font-size 1.9rem
        display inline-block
    &:active
      transform translate(-2%, -47%)
      box-shadow 0 1rem 2rem rgba(0, 0, 0, 0.15)
    &:focus
      outline none
    @media screen and (min-width sm)
      width auto
      transform translate(-50%)
      left 50%
      font-size 1.6rem
      padding 0.7rem 2.5rem
      border-radius 50rem
      &::first-letter
        font-size 2.4rem
        display inline-block
        margin-right 0.7rem
      &:active
        transform translate(-50%, 3px)
        box-shadow 0 1rem 2rem rgba(0, 0, 0, 0.15)
      &:focus
        outline none
      @media screen and (min-width lg)
        font-size 1.8rem
  .btn--new
    top 45%
    transform translateY(-50%)
    @media screen and (min-width sm)     
      top 1rem
      transform translate(-50%)
      left 50%
    @media screen and (min-width lg)     
      top 4rem
      transform translate(-50%)
      left 50%

  .btn--roll
    top 45%
    right 0
    transform translateY(-50%)
    @media screen and (min-width sm)
      transform translate(-50%)
      top 39.3rem
      left 50%
      max-width 30%
      font-size 1.6rem
    @media screen and (min-width lg)
      transform translate(-50%)
      max-width auto
      top 39.3rem
      left 50%
      font-size 1.8rem

  .btn--hold
    bottom 4rem
    right 0
    height 4rem
    &:active
      transform translate(-2%, 5%)
    @media screen and (min-width sm)
      top 46.1rem
      bottom auto
      left 50%
      height auto
      &:active
        transform translate(-50%, 3px)

</style>

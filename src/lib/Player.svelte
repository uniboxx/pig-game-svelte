<script>
  export let suffix;
  export let playerLabel;
  export let score;
  export let currentScore;
  export let active;
</script>

<section class="player {'player' + suffix}" class:player--active={active}>
  <h2 class="name" id={'name' + suffix}>{playerLabel}</h2>
  <p class="score" id={'score' + suffix}>{score}</p>
  <div class="current">
    <p class="current-label">Current</p>
    <p class="current-score" id={'current' + suffix}>{currentScore}</p>
  </div>
</section>

<style lang="stylus">
  @import '../../public/styl/_variables.styl'
  .player
    flex 1
    display flex
    flex-direction column
    align-items center
    padding 9rem
    transition all 0.75s
    @media screen and (min-width sm)
      padding 5rem
      

  .name
    position relative
    font-size 4rem
    text-transform uppercase
    letter-spacing 1px
    word-spacing 2px
    font-weight 300
    margin-bottom 1rem

  .score
    font-size 8rem
    font-weight 300
    color #c7365f
    margin-bottom auto

  .player--active
    background-color rgba(255, 255, 255, 0.4)
    .name
      font-weight 700
    .score
      font-weight 400
    .current
      opacity 1

  .current
    background-color #c7365f
    opacity 0.8
    border-radius 9px
    color #fff
    width 65%
    padding 2rem
    text-align center
    transition all 0.75s

  .current-label
    text-transform uppercase
    margin-bottom 1rem
    font-size 1.7rem
    color #ddd

  .current-score
    font-size 3.5rem

</style>

<script>
  export let suffix;
  export let playerLabel;
  export let score;
  export let currentScore;
  export let activePlayer;
  export let winnerPlayer;
</script>

<section class="player {'player' + suffix} {activePlayer} {winnerPlayer}">
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
    transition all 0.75s
    padding 2rem 1rem
    @media screen and (min-width sm)
      padding 5rem
      

  .name
    position relative
    font-size 2rem
    text-transform uppercase
    letter-spacing 1px
    word-spacing 2px
    font-weight 300
    @media screen and (min-width sm)
      font-size 4rem
      margin-bottom 1rem

  .score
    font-size 4rem
    font-weight 300
    color #c7365f
    @media screen and (min-width sm)
      font-size 8rem
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
    transition all 0.75s
    padding .2rem .5rem
    text-align center
    @media screen and (min-width sm)
      width 65%
      padding 2rem
      text-align center

  .current-label
    text-transform uppercase
    font-size .8rem
    color #ddd
    @media screen and (min-width sm)
      font-size 1.7rem
      margin-bottom 1rem
      

  .current-score
    font-size 2.5rem
    padding 0 1.5rem
    @media screen and (min-width sm)
      font-size 3.5rem
      padding 0

  .player--winner
    background-color #2f2f2f
    .name
      font-weight 700
      color #c7365f
</style>

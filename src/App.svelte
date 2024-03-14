<script>
  import Player from './lib/Player.svelte';
  import Button from './lib/Button.svelte';

  let active;
</script>

<Player
  suffix="--0"
  playerLabel="Player 1"
  score="43"
  currentScore="0"
  active="true" />
<Player
  suffix="--1"
  playerLabel="Player 2"
  score="24"
  currentScore="0"
  active="false" />

<img src="img/dice-5.png" alt="Playing dice" class="dice" />

<Button btnClass="btn--new" btnLabel="🔄 New game" />
<Button btnClass="btn--roll" btnLabel="🎲 Roll dice" />
<Button btnClass="btn--hold" btnLabel="📥 Hold" />

<style lang="stylus">
  @import '../public/styl/_variables.styl'
  .dice
    position absolute
    left 50%
    top 16.5rem
    transform translateX(-50%)
    height 10rem
    box-shadow 0 2rem 5rem rgba(0, 0, 0, 0.2)

  .player--winner
    background-color #2f2f2f
    .name
      font-weight 700
      color #c7365f
</style>

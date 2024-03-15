<script>
  import Player from './lib/Player.svelte';
  import Button from './lib/Button.svelte';

  const playerActive = 'player--active';
  let score0,
    score1,
    current0,
    current1,
    randomN,
    hideDice = true,
    src,
    currentPlayer,
    player1,
    player2,
    active0,
    active1,
    current,
    score;

  // $: randomN, console.log(randomN);

  function selectPlayer() {
    if (currentPlayer === 0) {
      active0 = playerActive;
      active1 = '';
    } else {
      active0 = '';
      active1 = playerActive;
    }
  }

  function newGame() {
    score0 = score1 = current0 = current1 = current = 0;
    currentPlayer = Math.floor(Math.random() * 2);
    selectPlayer();

    hideDice = true;
  }
  newGame();

  function rollDice() {
    randomN = Math.ceil(Math.random() * 6);
    src = `img/dice-${randomN}.png`;
    hideDice = false;
    if (randomN === 1) {
      current0 = current1 = 0;
      return changePlayer();
    } else {
      if (currentPlayer === 0) {
        current0 += randomN;
      } else {
        current1 += randomN;
      }
    }
    console.log(randomN, current);
  }

  function holdScore() {
    if (currentPlayer === 0) {
      score0 += current0;
      current0 = 0;
    } else {
      score1 += current1;
      current1 = 0;
    }
    changePlayer();
  }

  function changePlayer() {
    currentPlayer = currentPlayer === 0 ? 1 : 0;
    selectPlayer();
    console.log(currentPlayer);
  }
</script>

<Player
  suffix="--0"
  playerLabel="Player 1"
  score={score0}
  currentScore={current0}
  class={active0} />
<Player
  suffix="--1"
  playerLabel="Player 2"
  score={score1}
  currentScore={current1}
  class={active1} />

<img {src} alt="Playing dice" class="dice" class:hidden={hideDice} />

<Button btnClass="btn--new" btnLabel="🔄 New game" on:click={newGame} />
<Button btnClass="btn--roll" btnLabel="🎲 Roll dice" on:click={rollDice} />
<Button btnClass="btn--hold" btnLabel="📥 Hold" on:click={holdScore} />

<style lang="stylus">
  @import '../public/styl/_variables.styl'
  .dice
    position absolute
    height 4rem
    left 50%
    top 50%
    transform translate(-50%,-50%)
    &.hidden
      display none

    @media screen and (min-width sm) 
      transform translate(-50%)
      height 10rem
      top 16.5rem
      box-shadow 0 2rem 5rem rgba(0, 0, 0, 0.2)

  .player--winner
    background-color #2f2f2f
    .name
      font-weight 700
      color #c7365f
</style>

<script>
  import Player from './lib/Player.svelte';
  import Button from './lib/Button.svelte';

  const playerActive = 'player--active';
  const scoreToWin = 100;
  let currentPlayer,
    hideDice,
    randomN,
    src,
    active0,
    active1,
    current0,
    current1,
    score0,
    score1,
    winner0,
    winner1;

  function selectPlayer() {
    active0 = currentPlayer === 0 ? playerActive : '';
    active1 = currentPlayer === 0 ? '' : playerActive;
  }

  function newGame() {
    score0 = score1 = current0 = current1 = 0;
    winner0 = winner1 = '';
    currentPlayer = Math.floor(Math.random() * 2);
    hideDice = true;
    selectPlayer();
  }
  newGame();

  function rollDice() {
    if (winner0 || winner1) return;
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
  }

  function holdScore() {
    if (winner0 || winner1) return;
    if (currentPlayer === 0) {
      score0 += current0;
      if (score0 >= scoreToWin) {
        winner0 = 'player--winner';
      }
      current0 = 0;
    } else {
      score1 += current1;
      if (score1 >= scoreToWin) {
        winner1 = 'player--winner';
      }
      current1 = 0;
    }
    changePlayer();
  }

  function changePlayer() {
    currentPlayer = currentPlayer === 0 ? 1 : 0;

    selectPlayer();
  }
</script>

<Player
  suffix="--0"
  playerLabel="Player 1"
  score={score0}
  currentScore={current0}
  isActive={active0}
  winnerPlayer={winner0} />
<Player
  suffix="--1"
  playerLabel="Player 2"
  score={score1}
  currentScore={current1}
  isActive={active1}
  winnerPlayer={winner1} />

<img {src} alt="Playing dice" class="dice" class:hidden={hideDice} />

<Button btnClass="btn--new" btnLabel="🔄 New game" on:click={newGame} />
<Button btnClass="btn--roll" btnLabel="🎲 Roll dice" on:click={rollDice} />
<Button btnClass="btn--hold" btnLabel="📥 Hold" on:click={holdScore} />
<div class="info">
  <p>
    Se esce 1 perdi i punti accumulati! Vince chi arriva a {scoreToWin} punti!
  </p>
  <p>by uniboxx</p>
</div>

<style lang="stylus">
  @import '../public/styl/_variables.styl'
  .dice
    position absolute
    height 4rem
    left 50%
    top 50%
    transform translate(-50%,-100%)
    &.hidden
      display none

    @media screen and (min-width sm) 
      transform translate(-50%)
      height 10rem
      top 16.5rem
      box-shadow 0 2rem 5rem rgba(0, 0, 0, 0.2)

  
  .info
    display flex
    justify-content space-between
  .info 
    color #fff
    padding .5rem
    text-align center
    background-color #666
    opacity .8
    @media screen and (min-width sm)
      position absolute
      bottom 1rem
      left 50%
      transform translateX(-50%)
      width 100%
      font-size 1.3rem
</style>

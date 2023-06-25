<script>
  import { onMount } from "svelte";
  
  let countDownDate = new Date("Sep 6, 2023 00:00:00").getTime();
  
  let days = 0;
  let hours = 0;
  let minutes = 0;
  let seconds = 0;

  onMount(() => {
    let interval = setInterval(() => {
      let now = new Date().getTime();
      
      let distance = countDownDate - now;
      
      days = Math.floor(distance / (1000 * 60 * 60 * 24));
      hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
      seconds = Math.floor((distance % (1000 * 60)) / 1000);
      
      if (distance < 0) {
        clearInterval(interval);
      }
    }, 1000);
    
    return () => {
      clearInterval(interval);
    }
  });
</script>

<div class="countdown">
  <div class="time">{days}<span>Days</span></div>
  <div class="time">{hours}<span>Hours</span></div>
  <div class="time">{minutes}<span>Minutes</span></div>
  <div class="time">{seconds}<span>Seconds</span></div>
</div>

<style>
  .countdown {
    display: flex;
    justify-content: center;
    gap: 20px;
    font-size: 2em;
  }
  
  .time span {
    display: block;
    font-size: 0.5em;
  }
</style>

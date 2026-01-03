# intuitive-clock

Problem: i kept losing track of time, especially when im brainrotting so i needed some way to visually and intuitively see how much time had passed, instead of seeing a number and needing to do math in my brain to calculate how much time i had used up
Solution: this clock thing!! the outer ring fills up once a day, with the color of the sky! the middle ring is for the hour, and it slowly changes color as it fills up. the inner one shows each second that passes

## task.html is the most updated version
<img width="759" height="727" alt="image" src="https://github.com/user-attachments/assets/e743f8ff-1b67-44ce-bdf2-1ba5cac60107" />


**Glass UI!!! much fancy** <br>
<img width="338" height="387" alt="image" src="https://github.com/user-attachments/assets/4eb176e2-7bc4-4f70-9c79-0d4af1de1ed0" />


### todo
* add a settings thing for different beep sounds

```
function beep(){
  const ctx = new (window.AudioContext||webkitAudioContext)();
  [880, 988].forEach((freq, i) => {               // A5 → B5
    const o = ctx.createOscillator();
    const g = ctx.createGain();
    o.type = 'square'; o.frequency.value = freq;
    g.gain.value = 0.12;
    o.connect(g).connect(ctx.destination);
    o.start(ctx.currentTime + i * 0.06);
    o.stop(ctx.currentTime + i * 0.06 + 0.06);
  });
}

beep = function(){const ctx = new (window.AudioContext||webkitAudioContext)();
  [880, 988].forEach((freq, i) => {               // A5 → B5
    const o = ctx.createOscillator();
    const g = ctx.createGain();
    o.type = 'square'; o.frequency.value = freq;
    g.gain.value = 0.12;
    o.connect(g).connect(ctx.destination);
    o.start(ctx.currentTime + i * 0.06);
    o.stop(ctx.currentTime + i * 0.06 + 0.06);
  });}
```
```
const ctx = new (window.AudioContext||webkitAudioContext)();
  const osc = ctx.createOscillator();
  const gain = ctx.createGain();
  osc.type = 'triangle';
  osc.frequency.setValueAtTime(400, ctx.currentTime);
  gain.gain.setValueAtTime(0.3, ctx.currentTime);
  gain.gain.exponentialRampToValueAtTime(0.0001, ctx.currentTime + 0.08);
  osc.connect(gain).connect(ctx.destination);
  osc.start(); osc.stop(ctx.currentTime + 0.08);
```

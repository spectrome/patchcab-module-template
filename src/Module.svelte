<script lang="ts">
  import { Oscillator } from 'Tone';
  import { Faceplate, Knob, Patch } from '@patchcab/core';

  export let state = {
    freqency: 440,
  };

  const oscillator = new Oscillator(state.freqency, 'sine').start();

  $: oscillator.frequency.value = state.freqency;
</script>

<Faceplate title="MOD" color="#1D1E22">
  <Knob label="Frequency" x={20} y={60} bind:value={state.freqency} min={440} max={2400} steps={280} />
  <Patch label="out" x={40} y={320} name="audio-out" output={oscillator} />
</Faceplate>

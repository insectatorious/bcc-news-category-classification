<script>
  import { Progress } from 'sveltestrap';

  export let score = 0.0;
  export let emphasise = false;

  $: color = emphasise ? "success" : "info";
</script>

<Progress
  value={score * 100}
  {color}
  style="height: 20px">
  {score.toFixed(4)}
</Progress>

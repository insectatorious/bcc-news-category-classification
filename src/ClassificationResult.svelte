<script>
  import { Col, Container, Row, Progress, Card, CardBody } from 'sveltestrap';
  import { tweened } from 'svelte/motion';
	import { cubicOut } from 'svelte/easing';

  export let businessScore = 0.2;
  export let entertainmentScore = 0.2;
  export let sportScore = 0.2;
  export let techScore = 0.2;
  export let politicsScore = 0.2;
  export let visible = false;

  $: scores = [{"name": "Business", "score": businessScore},
               {"name": "Entertainment", "score": entertainmentScore},
               {"name": "Sport", "score": sportScore},
               {"name": "Tech", "score": techScore},
               {"name": "Politics", "score": politicsScore}];

  const progress = tweened(0, {
		duration: 400,
		easing: cubicOut
	})

</script>

{#if visible}
  <Container>
    <!-- <Card body> -->
      {#each scores as score}
        <!-- {score.score * 100} -->
        <Row>
          <Col sm="4" style="text-align: left">
            {score.name}
          </Col>
          <Col sm="8">
            <div class="progress" style="height: 15px">
              <div class="progress-bar"
                   role="progressbar"
                   style="width: {score.score * 100}%"
                   aria-valuenow="{score.score}"
                   aria-valuemin="0"
                   aria-valuemax="100">
                   {score.score}
                 </div>
            </div>
            <!-- <Progress color="info" height=15 value={score.score * 100}>{score.score}</Progress> -->
            <!-- <Progress color="info" value={score.score * 100} /> -->
          </Col>
        </Row>
      {/each}
    <!-- </Card> -->
  </Container>
{/if}

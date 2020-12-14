<script>
  import ClassScore from './ClassScore.svelte';
  import { Container, Row, Col } from 'sveltestrap';

  export let businessScore = 0;
  export let entertainmentScore = 0;
  export let sportScore = 0;
  export let techScore = 0;
  export let politicsScore = 0;
  export let visible = false;

  $: scores = [{"name": "Business", "score": businessScore},
               {"name": "Entertainment", "score": entertainmentScore},
               {"name": "Sport", "score": sportScore},
               {"name": "Tech", "score": techScore},
               {"name": "Politics", "score": politicsScore}];

  $: maxScoreCategory = scores.reduce((a, b) => a.score > b.score ? a : b);
  $: showMaxCategory = maxScoreCategory.score > 0.5;

</script>


<Container fluid>
  {#each scores as category}
    <Row>
      <Col sm="4" style="text-align: left">
        {#if showMaxCategory && maxScoreCategory.name == category.name}
          <strong>{category.name}</strong>
        {:else}
          {category.name}
        {/if}
      </Col>
      <Col sm="8">
        {#if maxScoreCategory.name == category.name}
          <ClassScore score={category.score} emphasise={showMaxCategory} />
        {:else}
          <ClassScore score={category.score} />
        {/if}
      </Col>
    </Row>
  {/each}
</Container>

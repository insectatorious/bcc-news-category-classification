<script lang="ts">
  import { tweened } from 'svelte/motion';
  import { quadIn } from 'svelte/easing';
  import {
    Col,
    Container,
    Row,
    Input,
    FormGroup,
    Progress,
    Label,
    Button,
    Card,
    CardBody
  } from 'sveltestrap';
  import ModelResults from './ModelResults.svelte'


  let articleText = null;
  let result = null;
  let showResult = false;
  let businessScore = 0.;
  let entertainmentScore = 0.;
  let sportScore = 0.;
  let techScore = 0.;
  let politicsScore = 0.;
  let waiting = false;
  let classificationTime = 21;
  let timer = resetTimer(0);

  $: btnText = waiting ? `Waiting for model` : "Classify";
  $: btnColour = waiting ? "secondary" : "primary";

  setInterval(() => {
    if ($timer > 0) $timer--;
  }, 1000);

  function resetScores() {
    businessScore = 0;
    entertainmentScore = 0;
    sportScore = 0;
    techScore = 0;
    politicsScore = 0;
  }


  function resetTimer(duration) {
    return tweened(duration, {
	    // duration: 400,
      easing: quadIn
	  })
  }

  function newClassification() {
    resetScores();
    waiting = true;
    timer = resetTimer(classificationTime);
  }

  async function getClassification () {
    newClassification();

		const res = await fetch(
      'https://europe-west2-project-radio-292312.cloudfunctions.net/bbc_news_classifier?' +  new URLSearchParams({
        "message": articleText
      }));

		const resJson = await res.json()
    waiting = false;
    timer = resetTimer(0);
		result = JSON.stringify(resJson)

    if (result != "") {
      showResult = true;
      businessScore = resJson.business;
      entertainmentScore = resJson.entertainment;
      sportScore = resJson.sport;
      techScore = resJson.tech;
      politicsScore = resJson.politics;
    }
	}
</script>

<Container fluid>
  <Row class="justify-content-center">
    <Col lg=8 xs=12>
      <!-- {#if waiting && $timer > 0} -->
        <Progress
          value={classificationTime - $timer}
          max={classificationTime}
          min={0}></Progress>
      <!-- {/if} -->
      <Card body>

        <Row>
          <Col>
              <FormGroup>
                <!-- <Label for="exampleText">👇 Text to Classify 👇</Label> -->
                <Input type="textarea"
                       name="text"
                       id="exampleText"
                       maxlength=1024
                       rows=7
                       required
                       bind:value={articleText}
                       placeholder="News article text goes here ..."  />
              </FormGroup>
          </Col>
        </Row>

        <Row>
          <Col>
            <Button
              color={btnColour}
              class="btn-block btn-lg btn-raised"
              on:click={getClassification}>
                {btnText}
            </Button>
          </Col>
        </Row>
      </Card>
    </Col>
  </Row>

  <br />
  <Row class="justify-content-center">
    <Col sm=12 lg=8  class="text-md-left">
      <h4>Results</h4>
    </Col>
  </Row>
  <Row class="justify-content-center">
    <Col sm=12 lg=8>
        <ModelResults
          visible={showResult}
          {businessScore}
          {entertainmentScore}
          {sportScore}
          {techScore}
          {politicsScore} />
    </Col>
  </Row>

</Container>

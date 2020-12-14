<script>
  import {
    Container,
    Row,
    Col,
    Card,
    CardBody,
    Badge
  } from 'sveltestrap';

</script>

<Container>
  <Row class="justify-content-center">
    <Col lg=6>
      <h4 class="display-4">News Article Classification</h4>
    </Col>
  </Row>
  <Row class="justify-content-center">
    <Col lg="6">


        <p class="text-md-left">
          A <a href="https://huggingface.co/transformers/model_doc/distilbert.html"
               rel="external"
               target="_blank">pre-trained</a>
          <a href="https://arxiv.org/abs/1910.01108"
             rel="external"
             target="_blank">DistilBert</a>
          model was
          <a href="https://huggingface.co/transformers/custom_datasets.html"
             rel="external"
             target="_blank">fine-tuned</a>
          on the
          <a href="http://mlg.ucd.ie/datasets/bbc.html"
             rel="external"
             taget="_blank">BBC News Category dataset</a>.
          With an 80-20 split, the fine-tuned model has a 0.9888 accuracy and
          an F1 Score of 0.9887 on the validation set.

          Categories:
            <em>business</em>,
            <em>entertainment</em>,
            <em>sport</em>,
            <em>tech</em>
            and <em>politics</em>.
        </p>

        <p class="small text-md-left"
           style="color:var(--gray)">
          Note: the model is hosted behind a GCP cloud function.
          A cold start will require upto 20 seconds to load the model.
          If already loaded, classification takes ~2 seconds.
        </p>

    </Col>
  </Row>
  <!-- <Row>
    <Col lg="6">
    </Col>
  </Row> -->
</Container>

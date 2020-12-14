<script>
  import { Container, Row, Col, Table } from 'sveltestrap';
</script>

<Container>
  <Row class="justify-content-center">
    <Col lg=6>
      <h4>Model Information</h4>
    </Col>
  </Row>
  <Row class="justify-content-center">
    <!-- <h5 class="display-4">Model Information</h5> -->

    <p class="text-left">
      TensorFlow backed, trained on Google Colab with GPU. 
    </p>
  </Row>

  <Row class="justify-content-center">
    <Col lg=8>
      <Table>
        <thead>
            <tr>
              <th>Split Type</th>
              <th>Num. of Datapoints</th>
              <th>Loss</th>
              <th>Accuracy</th>
              <th>F1 Score<th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <th scope="row">Train</th>
              <td>1780</td>
              <td>0.0756</td>
              <td>0.9820</td>
              <td>0.9938</td>
            </tr>
            <tr>
              <th scope="row">Validation</th>
              <td>445</td>
              <td>0.0428</td>
              <td>0.9888</td>
              <td>0.9887</td>
            </tr>
          </tbody>
      </Table>
    </Col>
  </Row>
  <Row class="justify-content-center">
    <Col lg=10>
      <p>Pre-trained model provided by HuggingFace
        <img src="https://huggingface.co/front/assets/huggingface_logo.svg"
             alt="HuggingFace Logo"
             height="28px"><img><br />

      <a href="https://huggingface.co/transformers/model_doc/distilbert.html"
         rel="external"
         target="_blank">
       https://huggingface.co/transformers/model_doc/distilbert.html</a>
     </p>
    </Col>
  </Row>
</Container>

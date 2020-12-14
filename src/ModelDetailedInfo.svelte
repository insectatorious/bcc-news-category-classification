<script>
  import { Container, Row, Col, Table } from 'sveltestrap';
</script>

<Container fluid>
  <!-- <Row class="justify-content-center">
    <Col xs=12 lg=6>
      <h4>Model Information</h4>
    </Col>
  </Row> -->

  <Row class="justify-content-center">
    <Col sm=12 lg=8 class="text-md-left">
      <h5>Model & Data Information</h5>
    </Col>
  </Row>
  <Row class="justify-content-center">
    <Col xs=12 lg=8>
      <div class="text-md-left">
        <!-- TensorFlow backed, trained on Google Colab with GPU. -->
        <dl class="row">
          <dt class="col-sm-3">Model</dt>
          <dd class="col-sm-9">DistilBert, a distilled version of BERT</dd>

          <dt class="col-sm-3">Backend</dt>
          <dd class="col-sm-9">TensorFlow, trained on Google Colab with GPU</dd>

          <dt class="col-sm-3">Category Count</dt>
          <dd class="col-sm-9">
            <Table class="table-sm">
              <thead>
                <tr>
                  <th>Class</th>
                  <th>Num. of Datapoints</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>Business</td>
                  <td>510</td>
                </tr>
                <tr>
                  <td>Entertainment</td>
                  <td>386</td>
                </tr>
                <tr>
                  <td>Sport</td>
                  <td>511</td>
                </tr>
                <tr>
                  <td>Tech</td>
                  <td>401</td>
                </tr>
                <tr>
                  <td>Politics</td>
                  <td>417</td>
                </tr>
              </tbody>
            </Table>

          </dd>
        </dl>
      </div>
    </Col>
  </Row>

  <Row class="justify-content-center">
    <Col xs=12 lg=8>
      <h5>Training Results</h5>
    </Col>
  </Row>

  <Row class="justify-content-center">
    <Col xs=12 lg=8>
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
    <Col lg=8 class="text-center">
      <p>Pre-trained model provided by HuggingFace
        <img src="https://huggingface.co/front/assets/huggingface_logo.svg"
             alt="HuggingFace Logo"
             height="28px" /><br />

      <a href="https://huggingface.co/transformers/model_doc/distilbert.html"
         rel="external"
         target="_blank">
       https://huggingface.co/transformers/model_doc/distilbert.html</a>
     </p>
    </Col>
  </Row>
</Container>

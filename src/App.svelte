<svelte:head>
	<!-- <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootswatch/4.5.2/sketchy/bootstrap.min.css"> -->
	<!-- <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootswatch/4.5.2/darkly/bootstrap.min.css"> -->


	<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700|Material+Icons">
	<link rel="stylesheet" href="https://unpkg.com/bootstrap-material-design@4.1.1/dist/css/bootstrap-material-design.min.css" integrity="sha384-wXznGJNEXNG1NFsbm0ugrLFMQPWswR3lds2VeinahP8N0zJw9VWSopbjv2x7WCvX" crossorigin="anonymous">

</svelte:head>

<script>
	import ModelInput from './ModelInput.svelte'
	import ModelInfo from './ModelInfo.svelte'
	import ModelDetailedInfo from './ModelDetailedInfo.svelte'
</script>


<main class="mx-3 px-0">
	<ModelInfo /> <br />
	<ModelInput /> <br />
	<ModelDetailedInfo />
</main>

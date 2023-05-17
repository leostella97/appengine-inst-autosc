# Deploy de Aplicação AppEngine com Instance Class Personalizado e Auto Scaling

<table>
	<ol>
		<li>Configure o ambiente do GCP: Certifique-se de ter uma conta no Google Cloud Platform e um projeto configurado.
			<br>
		<li>Prepare a aplicação: Verifique se a sua aplicação está pronta para ser implantada no App Engine. Certifique-se de ter o arquivo app.yaml configurado corretamente, com as informações necessárias sobre a sua aplicação.
			<br>
		<li>Defina a classe de instância personalizada: No arquivo app.yaml, você pode especificar a classe de instância personalizada usando a diretiva instance_class. Por exemplo: (arquivo yaml)

	runtime: python39
	instance_class: F4_HIGHMEM

<p>Nesse exemplo, estamos usando a classe de instância F4_HIGHMEM, que é uma classe personalizada que oferece recursos de memória adicionais.</p>

<li>Configure o escalonamento automático: Para configurar o escalonamento automático, você pode usar as diretivas automatic_scaling no arquivo app.yaml. Por exemplo: (arquivo yaml)

	automatic_scaling:
  	target_cpu_utilization: 0.65
  	min_instances: 1
  	max_instances: 10
    cool_down_period_sec: 180

<p>Nesse exemplo, estamos configurando o escalonamento automático com base na utilização da CPU. O App Engine manterá a utilização da CPU em torno de 65% e ajustará automaticamente o número de instâncias entre 1 e 10. O período de espera entre ajustes é de 180 segundos.</p>

<li> Implante a aplicação: Use o comando gcloud app deploy para implantar a sua aplicação no App Engine. Certifique-se de estar no diretório raiz da aplicação e execute o seguinte comando no terminal:

	gcloud app deploy

<p>O comando irá enviar a sua aplicação para o App Engine e configurar o ambiente conforme especificado no arquivo app.yaml.</p>

<li>Monitore a escalabilidade: Após o deploy da aplicação, você pode monitorar o escalonamento automático no Console do GCP. Você pode visualizar o número de instâncias em execução, a utilização da CPU e outras métricas relevantes para garantir que o escalonamento esteja ocorrendo conforme o esperado.
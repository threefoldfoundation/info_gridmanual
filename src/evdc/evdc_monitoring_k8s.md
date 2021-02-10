# Monitor K8s clusters 
TODO GEERT
- intro: explain what you can monitor in terms of k8s monitoring
- intro: explain what you can do either monitoring online or locally
- getting started: at the end add link to vdc_monitoring_stack.md
- getting started:  add link to monitoring_local.md

------------

The health of the VDC you deploy can be monitored. A stack has been prepared that offers monitoring through Prometheus and Grafana. A Helm chart `kube-prometheus-stack` is available, which offers Prometheus and Grafana as tooling to monitor your VDC. 

## Monitoring Manuals

The monitoring stack is available as a solution in the marketplace. 

![](img/evdc_k8s_monitoring_01_mktpl.png) 

Click `Deploy` and go through a simple chatflow to configure the monitoring on your cluster. 

![](img/evdc_k8s_monitoring_02_mktpl2.png)

A few elements need to be provided. 
First give your monitoring the name you want (will be part of the url).

![](img/evdc_k8s_monitoring_03_name.png)

You can configure the url to be auto-generated, or part of your own domain. 

![](img/evdc_k8s_monitoring_04_subdomain.png)

This information is enough to prepare the Monitoring Stack. 

![](img/evdc_k8s_monitoring_05_deploying.png)

Choose the size of the hardware to be reserved for your monitoring solution. 

![](img/evdc_k8s_monitoring_06_flavour.png)

Now there is enough information to set up the monitoring stack on your Kubernetes cluster. 

![](img/evdc_k8s_monitoring_07_init.png)

And that's it: the url's are available to access your monitoring solution, with both UIs on Prometheus and Grafana. 

![](img/evdc_k8s_monitoring_08_success.png)

![](img/evdc_k8s_monitoring_09_prometheus.png)

![](img/evdc_k8s_monitoring_09_grafana1.png)

![](img/evdc_k8s_monitoring_11_grafana3.png)

Alternatively you can also set up monitoring from your local computer, as an example through the [Lens](https://k8slens.dev/) IDE. To configure the K8S into Lens, you need to download the VDC `Kubeconfig` file. 

![](img/evdc_k8s_monitoring_12_kubeconfig.png)

Import this file into the IDE.

![](img/evdc_k8s_monitoring_13_lens_kubeconfig.png)

And you're done !

![](img/evdc_k8s_monitoring_14_lens.png)

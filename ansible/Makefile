.PHONY: applications_namespace server_deployment server_build eks_up eks_down eks_cluster_up eks_cluster_down eks_cluster_add_nodes eks_cluster_set_up eks_cluster_kubernetes_dashboard_up eks_cluster_kubernetes_dashboard_down eks_cluster_demo_application_up eks_cluster_demo_application_down eks_cluster_kubernetes_metric_service_up eks_cluster_kubernetes_metric_service_down

ANSIBLE_CONFIG=./ansible.cfg

applications_namespace:
	ansible-playbook applications_namespace.yml -v

eks_up: eks_cluster_up eks_cluster_set_up eks_cluster_add_nodes eks_cluster_kubernetes_dashboard_up

eks_down: eks_cluster_down

eks_cluster_up: 
	ansible-playbook eks_cluster.yml --extra-vars "eks_cluster_state=present" -v

eks_cluster_down: 
	ansible-playbook eks_cluster.yml --extra-vars "eks_cluster_state=absent" --tags "cloudformation" -v

eks_cluster_add_nodes:
	ansible-playbook eks_cluster_add_nodes.yml -v

eks_cluster_set_up:
	ansible-playbook eks_cluster_set_up.yml -v

eks_cluster_kubernetes_dashboard_up:
	ansible-playbook eks_cluster_kubernetes_dashboard.yml -v --extra-vars "kubernetes_dashboard_state=present"

eks_cluster_kubernetes_dashboard_down:
	ansible-playbook eks_cluster_kubernetes_dashboard.yml -v --extra-vars "kubernetes_dashboard_state=absent" 

eks_cluster_demo_application_up:
	ansible-playbook eks_cluster_demo_application.yml -v --extra-vars "demo_application_state=present"

eks_cluster_demo_application_down:
	ansible-playbook eks_cluster_demo_application.yml -v --extra-vars "demo_application_state=absent"

eks_cluster_kubernetes_metric_service_up:
	ansible-playbook eks_cluster_kubernetes_metric_service.yml -v --extra-vars "kubernetes_metrics_service_state=present"

eks_cluster_kubernetes_metric_service_down:
	ansible-playbook eks_cluster_kubernetes_metric_service.yml -v --extra-vars "kubernetes_metrics_service_state=absent"

server_build:
	ansible-playbook server_build.yml -v

server_deployment:
	ansible-playbook server_deployment.yml -v
# Kubernetes
This repository contains deployment scripts.

==> To check the pods
    kubectl get pods

NAME                                                   READY     STATUS    RESTARTS   AGE
alertmanager-prom-prometheus-operator-alertmanager-0   2/2       Running   0          13h
external-dns-7d746f7c5d-6dvh4                          1/1       Running   0          13h
postgres-84b5599f94-wpbpf                              1/1       Running   0          13h
prom-grafana-7d7bb56568-5tblr                          2/2       Running   0          13h
prom-kube-state-metrics-55bc76f8c4-d2gtm               1/1       Running   0          13h
prom-prometheus-node-exporter-7smcs                    1/1       Running   0          2h
prom-prometheus-node-exporter-cgmh9                    1/1       Running   0          2h
prom-prometheus-operator-operator-74c97465c-5gcg8      1/1       Running   0          13h
prometheus-prom-prometheus-operator-prometheus-0       3/3       Running   1          13h
redis-master-698964bc87-pfptw                          1/1       Running   0          13h
redis-slave-7f44d46cc5-2jfq9                           1/1       Running   0          13h
redis-slave-7f44d46cc5-9m2f2                           1/1       Running   0          13h
webapp-5db8c75fc9-m5p56                                1/1       Running   0          13h

==> To check the services
    kubectl get svc
    
NAME                                    TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)             AGE
alertmanager-operated                   ClusterIP   None            <none>        9093/TCP,6783/TCP   23h
kubernetes                              ClusterIP   10.19.240.1     <none>        443/TCP             1d
postgres                                ClusterIP   10.19.246.15    <none>        5432/TCP            1d
prom-grafana                            ClusterIP   10.19.241.136   <none>        80/TCP              1d
prom-kube-state-metrics                 ClusterIP   10.19.253.113   <none>        8080/TCP            1d
prom-prometheus-node-exporter           ClusterIP   10.19.253.221   <none>        9100/TCP            1d
prom-prometheus-operator-alertmanager   ClusterIP   10.19.250.191   <none>        9093/TCP            1d
prom-prometheus-operator-operator       ClusterIP   10.19.242.65    <none>        8080/TCP            1d
prom-prometheus-operator-prometheus     ClusterIP   10.19.242.181   <none>        9090/TCP            1d
prometheus-operated                     ClusterIP   None            <none>        9090/TCP            23h
redis-master                            ClusterIP   10.19.251.15    <none>        6379/TCP            1d
redis-slave                             ClusterIP   10.19.248.198   <none>        6379/TCP            1d
webapp                                  ClusterIP   10.19.242.159   <none>        80/TCP              1d
  
==> To check the ingress
    NAME              HOSTS                                    ADDRESS          PORTS     AGE
app-ingress       chatapp.webapps.saiapplications.online   35.193.***.***   80        1d
grafana-ingress   grafana.webapps.saiapplications.online   35.193.***.***   80        1d

==> To describe the pod
    kubectl describe pod webapp-5db8c75fc9-m5p56
    
Name:               webapp-5db8c75fc9-m5p56
Namespace:          default
Priority:           0
PriorityClassName:  <none>
Node:               gke-webapplication-chatapplication-po-a3dedcbe-n1xt/10.128.15.213
Start Time:         Tue, 23 Apr 2019 10:02:03 +0530
Labels:             app=webapp
                    pod-template-hash=1864731975
Annotations:        kubernetes.io/limit-ranger=LimitRanger plugin set: cpu request for container webapp
Status:             Running
IP:                 10.16.1.4
Controlled By:      ReplicaSet/webapp-5db8c75fc9
Containers:
  webapp:
    Container ID:   docker://358f30d0391c1153bdc0ff546b08f026214636ad4f9f3211a323e773b9c5b54c
    Image:          gcr.io/web-application-231505/new-chat:latest
    Image ID:       docker-pullable://gcr.io/web-application-231505/new-chat@sha256:a780c03b49a70d3ef08817769f3012007aa143f72ac4e6373ea4ce9a74feaa35
    Port:           8000/TCP
    Host Port:      0/TCP
    State:          Running
      Started:      Tue, 23 Apr 2019 10:02:46 +0530
    Ready:          True
    Restart Count:  0
    Requests:
      cpu:  100m
  
  
==> To check the logs of pod
    kubectl logs webapp-5db8c75fc9-m5p56od

Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying sessions.0001_initial... OK

119 static files copied to '/srv/chatapplication/static'.
Starting Gunicorn.
==> /srv/logs/access.log <==

==> /srv/logs/gunicorn.log <==
[2019-04-23 04:32:49 +0000] [1] [INFO] Starting gunicorn 19.9.0
[2019-04-23 04:32:49 +0000] [1] [INFO] Listening at: http://0.0.0.0:8000 (1)
[2019-04-23 04:32:49 +0000] [1] [INFO] Using worker: sync
[2019-04-23 04:32:49 +0000] [17] [INFO] Booting worker with pid: 17
[2019-04-23 04:32:49 +0000] [19] [INFO] Booting worker with pid: 19
[2019-04-23 04:32:49 +0000] [20] [INFO] Booting worker with pid: 20

    

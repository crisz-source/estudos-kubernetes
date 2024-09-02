## O projeto kubernetes, eu fiz feito em linux - ubuntu 22.04 e as imagens do projeto foi feita pela Alura. 

### Para verificar o conteúdo do projeto portal de notícias, siga esses passos:
##


#### 1 - instalando o kubectl
```Bash
sudo apt-get install kubectl --classic
#ou
sudo snap install kubectl --classic
```


#### 2 - instale o minikube para uma simulação de um cluster
```Bash
    curl -Lo minikube https://storage.googleapis.com/minikube/releases/v1.12.1/minikube-linux-amd64 \ && chmod +x minikube
    sudo install minikube /usr/local/bin/
```

#### 3 - Dê um start no minikube
```Bash
minikube start
```
#### 4 - Verifique o status 
```Bash
minikube status
```


# Aplicando os pods, services e configmaps

#### 1 - Entre no diretório do bando de dados e execute:

```Bash
kubectl apply -f db-configmap.yml
kubectl apply -f db-noticias.yml
kubectl apply -f db-svc-db-noticias.yml
```

#### 2 - Entre no diretório do backend e execute:

```Bash
kubectl apply -f sistema-configmap.yml
kubectl apply -f sistema-noticias.yml
kubectl apply -f svc-sistema-noticias.yml

```

#### 3 - Entre no diretório do frontend e execute: 
```Bash
kubectl apply -f portal-configmap.yml
kubectl apply -f portal-noticias.yml
kubectl apply -f svc-portal-noticias.yml

#será necessário mudar uma configuração no arquivo portal-configmap.yml

#Quando cria um node, ele pega um ip diferente e precisa adicionar neste campo no arquivo: 

# data:
# IP_SISTEMA: http://ip-node:30001 #URL da parte de notícias

#para verificar o ip, basta executar os seguinte comando:

kubectl get nodes -o wide

#pegue o INTERNAL-IP e adione em IP_SISTEMA para que frontend comunique com o backend 
```

#### 4 - Verifique se foi criado tudo corretamente
```Bash
kubectl get pods
kubectl get svc
kubectl get configmaps 
```

#### 


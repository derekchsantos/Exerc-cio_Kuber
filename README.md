# Exerc-cio_Kuber
Exercício Kuber

#ConfigMap. Variáveis do ambiente

apiVersion: v1  
kind: ConfigMap  
metadata:  
  name: my-config  
data:  
  app_config.yml: |  
    port: "8080"  
    log_level: "info"

#criação do secret

apiVersion: v1  
kind: Secret  
metadata:  
  name: my-secrets  
data:  
  database_password: BASE64ENCODEDPASSWORD

#my deployment

apiVersion: apps/v1  
kind: Deployment  
metadata:  
  name: my-app  
spec:  
  replicas: 3  
  selector:  
    matchLabels:  
      app: my-app  
  template:  
    metadata:  
      labels:  
        app: my-app  
    spec:  
      containers:  
      - name: my-app  
        image: nginx:latest  
        ports:  
        - containerPort: 80  
        env:  
        - name: LOG_LEVEL  
          valueFrom:  
            configMapKeyRef:  
              name: my-config  
              key: app_config.yml  
        envFrom:  
        - secretRef:  
            name: my-secrets

#my service

apiVersion: v1  
kind: Service  
metadata:  
  name: my-service  
spec:  
  selector:  
    app: my-app  
  ports:  
    - protocol: TCP  
      port: 80  
      targetPort: 80  
  type: LoadBalancer

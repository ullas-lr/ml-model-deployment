eval $(minikube docker-env)

docker build -t ollama-mistral:latest .

docker images

kubectl apply -f deployment.yaml

# Point your Docker to Minikube’s node
eval $(minikube docker-env)

# Confirm you are talking to Minikube’s Docker
docker images

# If `ollama-mistral:local` is NOT listed:
docker build -t ollama-mistral:local .

# Redeploy just to be sure
kubectl rollout restart deployment ollama-mistral

kubectl apply -f service.yaml

kubectl get svc

root@ip-172-31-31-96:~/ollama# minikube service ollama-mistral-svc --url
http://192.168.49.2:30134

curl http://192.168.49.2:30134/api/generate \
  -H "Content-Type: application/json" \
  -d '{
    "model": "mistral",
    "prompt": "Explain containers in one line."
  }'


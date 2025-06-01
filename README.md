# Kafka on Kubernetes

This repository provides the **most basic way** to deploy **Apache Kafka** on **Kubernetes**, ensuring a straightforward setup for development and testing environments.

## Features
- Minimal configuration for quick deployment
- Uses Kubernetes **StatefulSets** for Kafka brokers
- Includes **Zookeeper** for Kafka coordination
- Basic YAML manifests for easy application

## Prerequisites
Before deploying Kafka, ensure you have:
- A running **Kubernetes cluster**
- `kubectl` installed and configured
- **Helm** (optional, for managing dependencies)

## Deployment Steps
1. **Clone the repository**:
   ```sh
   git clone https://github.com/zarakM/kafka-kubernetes.git
   cd kafka-kubernetes
   ```

2. **Apply the Zookeeper manifest**:
   ```sh
   kubectl apply -f zookeeper.yaml
   kubectl apply -f zooservice.yaml
   ```

3. **Deploy Kafka**:
   ```sh
   kubectl apply -f kafka-docker.yaml
   kubectl apply -f kafka-service.yaml
   ```

4. **Verify the deployment**:
   ```sh
   kubectl get pods -n kafka
   ```

## Usage
Once deployed, you can interact with Kafka using:
- **Kafka CLI**:
  ```sh
  kubectl exec -it kafka-0 -- kafka-topics.sh --list --bootstrap-server kafka:9092
  ```
- **Port-forwarding for local access**:
  ```sh
  kubectl port-forward svc/kafka 9092:9092
  ```

## Cleanup
To remove the deployment:
```sh
kubectl delete -f kafka.yaml
kubectl delete -f zookeeper.yaml
```

## Contributing
Feel free to open issues or submit pull requests to improve this setup.

## License
This project is licensed under the **MIT License**.

---

Happy deploying! 🚀
```

This README provides a **clear** and **structured** guide for users to deploy Kafka on Kubernetes with minimal effort. Let me know if you'd like any refinements! 😊

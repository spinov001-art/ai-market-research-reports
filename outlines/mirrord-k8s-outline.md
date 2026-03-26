# Local Kubernetes Debugging with mirrord: Run Your Code As If It Were In the Cluster

## Summary
Every backend developer deploying to Kubernetes faces the same frustration: a 10-minute code-build-push-deploy cycle just to test a one-line fix. mirrord solves this by making your local process behave as if it is running inside the Kubernetes pod — intercepting live traffic, reading pod environment variables, and accessing the cluster filesystem in real-time. This tutorial shows how to set it up and integrate it into a real debugging workflow.

## Target Audience
Backend engineers and DevOps engineers who build microservices on Kubernetes.

## Outline

### 1. The Problem: Kubernetes Local Dev is Slow
- The typical dev loop: 10+ minutes per cycle
- Limitations of kubectl port-forward and kubectl exec
- Why "it works locally" often fails in cluster

### 2. What mirrord Does (and How)
- Intercepts network traffic from a running pod to your local process
- Injects pod environment variables into your local process
- Optionally proxies filesystem access
- Mirror mode vs. steal mode explained

### 3. Installation and Setup
- Install via CLI or VSCode/JetBrains extension
- Point at your kubeconfig
- Select target deployment/pod

### 4. Hands-On: Debugging a Python FastAPI Service
- Sample app: API that fetches and processes data from external sources
- Start local dev server, attach mirrord targeting staging pod
- Live traffic flows to local process
- Set breakpoint, inspect live request data, fix bug
- No image rebuild, no redeployment

### 5. Advanced: Header-Based Traffic Stealing
- Only steal requests with custom header (x-debug: 1)
- Production traffic unaffected
- Great for debugging production-only bugs safely

### 6. CI Integration Pattern
- Run integration tests with mirrord against ephemeral cluster
- Replaces mocking entirely for integration layer

### 7. Comparison: mirrord vs Telepresence vs Port-Forward
- Feature table
- When to use each

### 8. Conclusion
Estimated: ~1800 words + code snippets

## Author
Technical writer with 650+ published articles on Dev.to.
Portfolio: https://dev.to/spinov001 | GitHub: https://github.com/spinov001-art

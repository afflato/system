# Observability Guiding Principles

1. **Shared ownership Model**

    The Observability Platform must operate under a shared ownership model, with clearly defined responsibilities across platform, application, and infrastructure teams 

2. **Open-Source Tooling**

    a. **Open-Source Foundation** 
    
    All Observability Technologies must be based on open-source components with acceptable licenses (e.g., Apache 2.0) and active community support to ensure sustainability and transparency.

    b. **Application Runtime Compatibility for Signal Generation** 
    
    Observability Technologies responsible for generating observability signals (metrics, traces, logs) must be compatible with application runtimes commonly used in the development ecosystem (e.g Java, Python, etc.)

    c. **Deployment for Collection and Transport** 
    
    Observability Technologies related to data collection and transport must be deployable within the **Kubernetes ecosystem**, as well as on **non-Kubernetes platforms** and edge devices, to support diverse infrastructure environments.

    d. **Kubernetes-Native for Storage, Alerting, and Visualization** 
    
    Observability Technologies handling storage, alerting, and visualization must be deployable within the Kubernetes ecosystemn to ensure consistency, scalability, and operational efficiency.

3. **Hybrid Deployment Compatibility** 
Tooling must be operable both on-premises and in cloud environments (AWS/Azure), enabling consistent operational efficiency across deployment models 
4. **Security Compliance**
 All Observability Technologies must comply with organizational security policies and standards, including secure communication, authentication, and authorization mechanisms 
5. **Automated Deployment & Change Management**
 Dbservability tooling must be deployed and updated using automated mechanisms that support compliance with change management policies and minimize manual interventior 
6. **Self-Monitoring Capability**
 The platform must generate its own observability data to enable monitoring, performance tuning, and troubleshooting of the observability tooling itself 
7. **Avoidance of Vendor Lock-ln**
 Tooling choices must prioritize interoperability and portability to prevent dependency on any single vendor 
8. **Federated Monitoring & Alerting**
 fhe platform must support federated models for monitoring and alerting, allowing decentralized teams to operate independently while contributing to centralized visibility



# Observability Platform Technologies

| Capability     |   Technology |
|----------------|--------------|
|Generation: Metrics, Traces, logs  | OTel SDK |
| Propagation: Metrics, Traces, Logs | OTel Collector |
| Collection & Processina: Metrics | Prometheus |
| Collection & Processing: Traces | Jaeger Collector |
| Collection & Processing: Network Traces (SNMP) | Telegraph |
| Collection & Processing: Logs | To be finalized |
| Storage: Metrics (TSDB) | VictoriaMetrics |
| Storage: Traces | OpenSearch |
| Visualization: Metrics, Logs, Traces Correlation | Grafana |
| Visualization: Traces | Jaeger UI |
| Visualization: Logs | To be finalized |


Note: Additional technologies for edge devices and infrastructure (e.g., messaging systems) will be determined in future releases.

# Observability: Deployment Technologies: VM & Bare Meta
Observability in VM and Bare Metal environments can be viewed from two distinct perspectives:
## Infrastructure-Level Observability
This aspect focuses on monitoring the performance and usage of the underlying VM or bare metal machines. It is achieved by deploying agents directly on these machines. These gents collect machine-specific performance metrics such as CPU, memory, disk 1/O, and network usage. The collected data is then forwarded to a centralized Observability Cluster -- typically running on OpenShift or EKS -- where Prometheus and Jaeger controllers aggregate and visualize the metrics.
## Application-Level Observability
his aspect pertains to the observability of the technologies deployed on the infrastructure, such as Kafka, databases, or microservices. Each technology may require its owr bservability solution, tailored to its architecture and operational characteristics. These solutions typically include exporters, instrumentation libraries, and dashboards that provide insights into application-specific metrics, traces, and logs.
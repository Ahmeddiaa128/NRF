# NF Repository Function (NRF)
//===============================================================
 NF Repository Function. NF stands for Network Function, which is a fundamental component in network architecture, especially in 5G networks.

The NF Repository Function (nrf) is defined in the 3GPP specifications for 5G networks. It plays a crucial role in network function discovery, registration, and management within a 5G Core Network (5GC). The nrf provides a central repository where various network functions register themselves and discover other network functions, enabling dynamic network function orchestration and service composition.

In simpler terms, the nrf is responsible for keeping track of available network functions and their capabilities, facilitating the establishment and management of communication sessions in 5G networks. It allows for the dynamic deployment and scaling of network functions to meet the demands of different services and users.
//================================================================>

# Pipeline Overview
This Jenkins pipeline automates the build, testing, and deployment process for a Dockerized application using Jenkins, Docker, Helm, and AWS EKS.

## Pipeline Stages:
Verify Branch:

Displays the current Git branch being built.
### Login to Dockerhub:

Logs in to Dockerhub using stored credentials.
### Pulling base image from Dockerhub:

Pulls the latest base image from Dockerhub (abodiaa/nrf-base:latest).
### Docker Build:

Lists Docker images.
Builds a Docker image tagged as abodiaa/nrf:latest.
Lists Docker images again.
### Scan Image for Common Vulnerabilities and Exposures:

Scans the Docker image for common vulnerabilities and exposures using Trivy.
Generates a JSON report of vulnerabilities.
### Pushing to Dockerhub:

Pushes the built Docker image (abodiaa/nrf:latest) to Dockerhub.
### Build and Package Helm Chart:

Packages the Helm chart located in ./helm/.
### Configure Kubernetes Context:

Configures the Kubernetes context for AWS EKS cluster 5G-Core-Net.
### Deploy Helm Chart on EKS:

Upgrades or installs the Helm chart named nrf onto the EKS cluster.
## Post-build Actions:
### Always:
Archives the Trivy vulnerability report.
Removes Docker images (abodiaa/nrf:latest and abodiaa/nrf-base:latest).


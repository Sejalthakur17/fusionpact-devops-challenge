# Fusionpact DevOps Challenge – Sejal Thakur

## Project Overview
This project demonstrates a complete DevOps pipeline including containerization, cloud deployment, monitoring, and CI/CD automation. The application is deployed on AWS EC2 using Docker and Docker Compose, monitored using Prometheus and Grafana, and automated using Jenkins CI/CD pipeline.

## Architecture
(User → Nginx → Frontend → Backend → Prometheus → Grafana → Jenkins → DockerHub → EC2)

## Tools & Technologies Used
- AWS EC2
- Docker
- Docker Compose
- Nginx
- Prometheus
- Grafana
- Jenkins
- GitHub
- DockerHub

## Setup Instructions

### Clone Repository

git clone https://github.com/Sejalthakur17/fusionpact-devops-challenge.git

cd fusionpact-devops-challenge


### Run Application

docker-compose up -d


### Access Services
| Service | URL |
|--------|-----|
| Frontend | http://EC2-IP |
| Backend | http://EC2-IP:8000 |
| Prometheus | http://EC2-IP:9090 |
| Grafana | http://EC2-IP:3000 |
| Jenkins | http://EC2-IP:8080 |

## CI/CD Pipeline
The Jenkins pipeline automatically:
- Pulls code from GitHub
- Builds Docker images
- Pushes images to DockerHub
- Deploys application on AWS EC2

## Monitoring
Prometheus collects metrics from the backend and system containers. Grafana is used to visualize metrics such as CPU usage, memory usage, request rate, error rate, and latency.

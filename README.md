# EP3 - Kubernetes y CI/CD con GitHub Actions

## Descripción

Este repositorio contiene el desarrollo de la Evaluación Parcial N°3 del ramo **Introducción a Herramientas DevOps**.

El proyecto consiste en desplegar una aplicación contenedorizada sobre un clúster Kubernetes (k3s del laboratorio), implementar autoscaling mediante Horizontal Pod Autoscaler (HPA) y configurar un pipeline de Integración Continua (CI) utilizando GitHub Actions.

## Objetivos

* Desplegar una aplicación en Kubernetes.
* Utilizar un Deployment para administrar los Pods.
* Exponer la aplicación mediante un Service tipo LoadBalancer.
* Configurar escalamiento automático utilizando Horizontal Pod Autoscaler (HPA).
* Construir una imagen Docker y almacenarla en el registro local del laboratorio.
* Implementar un pipeline CI con GitHub Actions para automatizar la construcción de la imagen.

## Estructura del proyecto

```text
.
├── .github/
│   └── workflows/
│       └── deploy-eks.yml
├── Dockerfile
├── deployment.yaml
├── hpa.yaml
├── namespace.yaml
├── service.yaml
└── README.md
```

## Requisitos

* Kubernetes (k3s)
* kubectl
* Podman
* Git
* GitHub
* GitHub Actions

## Despliegue de la aplicación

Aplicar los manifiestos de Kubernetes:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f hpa.yaml
```

Verificar el estado de los recursos:

```bash
kubectl get all -n user18
```

Consultar el autoscaling:

```bash
kubectl get hpa -n user18
```

Validar el funcionamiento del servicio:

```bash
curl http://192.168.3.244
```

## Pipeline CI/CD

El proyecto incorpora un workflow de GitHub Actions ubicado en:

```text
.github/workflows/deploy-eks.yml
```

El pipeline realiza automáticamente:

* Checkout del repositorio.
* Construcción de la imagen Docker.
* Preparación del flujo para publicación y despliegue.

**Nota:** De acuerdo con la configuración del laboratorio, el despliegue al clúster Kubernetes se realiza manualmente desde el servidor k3s, ya que los runners hospedados por GitHub Actions no tienen acceso directo al entorno del laboratorio.

## Tecnologías utilizadas

* Kubernetes (k3s)
* Podman
* Dockerfile
* Git
* GitHub
* GitHub Actions

## Autores

Matilda Vargas, Juan Vargas
Ingeniería en Informática


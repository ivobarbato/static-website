# 📦 Despliegue de Sitio Web Estático en Kubernetes con Minikube

Este proyecto implementa un sitio web estático personalizado dentro de un entorno local usando **Minikube** y **Kubernetes**. Se utiliza una imagen Docker personalizada basada en **Nginx**, la cual contiene los archivos HTML y CSS del sitio.

💡 Nota: A diferencia de otras implementaciones que copian archivos manualmente dentro de Minikube, este proyecto incluye los archivos del sitio directamente en una imagen Docker personalizada. Por eso no es necesario usar comandos como `tar`, `minikube cp` o montar volúmenes persistentes.
---

## ✅ Requisitos Previos

- Docker Desktop
- Minikube
- kubectl
- Git Bash o PowerShell

---

## 📁 Estructura del Proyecto

```
TPcloud/
├── website-content/         # Contiene el sitio web estático + Dockerfile
│   ├── index.html
│   ├── style.css
│   ├── assets/
│   ├── Dockerfile
│   └── .dockerignore
└── k8s-manifests/           # Contiene los manifiestos de Kubernetes
    ├── deployment.yaml
    └── service.yaml
```

---

## 🚀 Pasos para Desplegar

### 1. Clonar ambos repositorios

```bash
git clone https://github.com/ivobarbato/website-content
git clone https://github.com/ivobarbato/k8s-manifests
```

### 2. Compartir la carpeta en Docker Desktop

Ir a:  
`Settings > Resources > File Sharing`  
Y asegurarse de que la carpeta `website-content` esté habilitada.

### 3. Iniciar Minikube

```bash
minikube start --driver=docker
```

Asegurate de tener Docker Desktop ejecutándose antes de este paso.

### 4. Construir la imagen de Docker personalizada

```bash
cd website-content
docker build -t ivowebsite:latest .
```

### 5. Aplicar los manifiestos de Kubernetes

```bash
cd ../k8s-manifests
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

### 6. Verificar que el pod esté corriendo

```bash
kubectl get pods
```

### 7. Acceder al sitio desde el navegador

```bash
minikube service website-service
```

Esto abrirá una nueva pestaña en tu navegador con el sitio web funcionando.

---

## 🧠 Notas Finales

- Este entorno simula un despliegue casi productivo usando herramientas reales de infraestructura.
- La imagen se construye localmente; no se utiliza un registry externo.
- Los manifiestos están separados por tipo (deployment y service) como buena práctica.
- Se asegura persistencia usando una imagen con contenido embebido.

---

## 👤 Desarrollado por

**Ivo Barbato**  
Entrega TP Cloud – Abril 2025  
Repositorio principal: [https://github.com/ivobarbato/static-website](https://github.com/ivobarbato/static-website)


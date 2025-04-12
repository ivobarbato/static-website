# 📦 Despliegue de Sitio Web Estático en Kubernetes con Minikube

Este proyecto implementa un sitio web estático personalizado dentro de un entorno local usando Minikube y Kubernetes. Se utiliza una imagen de Docker personalizada basada en Nginx, que contiene archivos HTML, CSS y recursos propios.

---

## 📁 Estructura del proyecto

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

## 🔧 Requisitos

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- Git

---

## 🚀 Pasos para levantar el entorno

1. Clonar ambos repositorios:
   ```bash
   git clone https://github.com/miusuario/website-content
   git clone https://github.com/miusuario/k8s-manifests
   ```

2. Abrir Docker Desktop y asegurarse de que la carpeta `website-content` esté compartida  
   (`Settings > Resources > File Sharing`).

3. Iniciar Minikube:
   ```bash
   minikube start
   ```

4. Construir la imagen de Docker personalizada:
   ```bash
   cd website-content
   docker build -t ivowebsite:latest .
   ```

5. Aplicar los manifiestos de Kubernetes:
   ```bash
   cd ../k8s-manifests
   kubectl apply -f .
   ```

6. Verificar que el pod esté corriendo:
   ```bash
   kubectl get pods
   ```

7. Acceder al sitio desde el navegador:
   ```bash
   minikube service website-service
   ```

---

## 📸 Capturas requeridas para la entrega

1. Estructura del proyecto (`TPcloud/`)
2. `minikube start` funcionando correctamente
3. `docker build` exitoso con `ivowebsite:latest`
4. Contenido del `Dockerfile`
5. Aplicación de los YAML (`kubectl apply -f .`)
6. Resultado de `kubectl get pods` mostrando el pod en `Running`
7. Dentro del pod: `ls -l /usr/share/nginx/html`
8. Sitio cargado en el navegador desde el servicio de Kubernetes
9. Contenido del `deployment.yaml` con:
   ```yaml
   image: ivowebsite:latest
   imagePullPolicy: Never
   ```
10. `README.md` en el repositorio

---

## ✅ Notas finales

- Este entorno simula un despliegue casi productivo usando herramientas reales de infraestructura.
- La imagen se construye localmente y no se sube a un registro remoto.
- Minikube permite hacer pruebas locales de manera simple sin necesidad de una nube.

---

🧠 Desarrollado por: **Ivo Barbato**  
📅 Entrega TP Cloud - Abril 2025

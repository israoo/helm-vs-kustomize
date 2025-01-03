# Helm vs. Kustomize

Este repositorio contiene ejemplos prácticos que demuestran las diferencias entre **Helm** y **Kustomize**, dos herramientas populares para gestionar manifiestos en Kubernetes. Los ejemplos están diseñados para ayudarte a entender cómo funcionan estas herramientas y cuándo utilizar cada una según tus necesidades.

---

## Estructura del repositorio

```plaintext
.
├── helm/
│   └── my-nginx-chart/
│       ├── templates/
│       │   └── deployment.yaml    # Plantilla para el Deployment
│       ├── values.yaml            # Valores predeterminados para personalización
│       └── Chart.yaml             # Metadatos del chart
└── kustomize/
    ├── base/                      # Configuración base de Kustomize
    └── overlays/production/       # Personalización específica para producción

---

## ¿Qué encontrarás en este repositorio?

### 1. Ejemplo de Helm

  - Un chart de Helm que despliega un Deployment de Nginx.
  - Instrucciones para instalar y personalizar el chart.

### 2. Ejemplo de Kustomize

  - Configuración base de Kustomize para un Deployment de Nginx.
  - Personalización específica para producción utilizando overlays.

---

## ¿Cómo utilizar este repositorio?

1. Clona este repositorio en tu máquina local.

    ```bash
    git clone https://github.com/israoo/helm-vs-kustomize.git
    cd helm-vs-kustomize
    ```

2. Explora los directorios `helm` y `kustomize` para ver los ejemplos.

3. Sigue las instrucciones en cada directorio para instalar y personalizar los manifiestos.

---

## Herramientas utilizadas

- **Helm**: Gestor de paquetes para Kubernetes.
- **Kustomize**: Herramienta para personalizar manifiestos de Kubernetes.

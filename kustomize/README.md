# 🎨 Kustomize: Despliegue de NGINX en Kubernetes

Este directorio contiene una configuración de **Kustomize** para desplegar un Pod de NGINX en Kubernetes. Está diseñado para ser simple y demostrar cómo usar Kustomize para personalizar manifiestos YAML.

---

## 📂 Estructura del proyecto

```plaintext
kustomize/
├── base/
│   ├── deployment.yaml          # Manifiesto base para el Deployment
│   └── kustomization.yaml       # Configuración base de Kustomize
└─ overlays/
    └── production/
        ├── kustomization.yaml   # Overlay para personalización en producción
        └── patch.yaml           # Cambios específicos para producción
```

---

## 🚀 Cómo usar esta configuración

### 1. Instalar kubectl con soporte para Kustomize

Asegúrate de tener kubectl instalado en tu máquina. Desde la versión 1.14 de Kubernetes, Kustomize está integrado en kubectl.

### 2. Aplicar la configuración base

La configuración base de Kustomize contiene un manifiesto simple para desplegar un Pod de NGINX con una sola réplica. Para aplicar esta configuración, ejecuta el siguiente comando desde el directorio base/:

```bash
kubectl apply -k base/
```

Este comando aplicará los recursos definidos en el manifiesto deployment.yaml dentro del directorio base/.

### 3. Inspeccionar los manifiestos

Puedes inspeccionar los manifiestos generados por Kustomize al aplicar los overlays. Para ello, puedes usar el siguiente comando:

```bash
kubectl kustomize overlays/production/
```

### 4. Aplicar una personalización (Overlay)

Si necesitas personalizar el despliegue para un entorno específico, como producción, puedes usar los overlays. Para aplicar la personalización definida en el directorio overlays/production/, usa el siguiente comando:

```bash
kubectl apply -k overlays/production/
```

Este overlay realiza los siguientes cambios:

- Aumenta el número de réplicas a 2.
- Actualiza la versión de la imagen de NGINX a 1.21.

---

## ⚙️ Personalización

Puedes personalizar los manifiestos base o crear nuevos overlays para distintos entornos. A continuación, un ejemplo del contenido de un overlay:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-nginx
spec:
  replicas: 5
```

En este ejemplo, el overlay únicamente aumenta el número de réplicas del Deployment a 5. Puedes crear tantos overlays como necesites para personalizar tu despliegue.

---

## 🧹 Eliminar los recursos

Para eliminar los recursos aplicados con Kustomize, usa el mismo comando que utilizaste para aplicarlos, pero con la opción delete:

```bash
kubectl delete -k base/
```

o, en el caso de un overlay:

```bash
kubectl delete -k overlays/production/
```

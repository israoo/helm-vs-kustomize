# Helm: Despliegue de NGINX en Kubernetes

Este directorio contiene un **chart de Helm** que despliega un Pod de NGINX en Kubernetes. El chart está diseñado para ser simple y demostrar cómo funciona Helm para empaquetar y gestionar configuraciones en Kubernetes.

---

## Estructura del chart

```plaintext
my-nginx-chart/
├── templates/
│   ├── deployment.yaml    # Plantilla para el Deployment
├── values.yaml            # Valores predeterminados para personalización
└── Chart.yaml             # Metadatos del chart
```

---

## Cómo usar este chart

### 1. Instalar Helm

Asegúrate de tener Helm instalado en tu máquina. Puedes seguir las instrucciones en la [documentación oficial](https://helm.sh/docs/intro/install/).

### 2. Inspeccionar los manifiestos

Puedes inspeccionar los manifiestos generados por el chart antes de aplicarlos en el clúster. Para ello, puedes usar el siguiente comando:

```bash
helm template my-nginx . -f values.yaml
```

El comando anterior debe ejecutarse desde el directorio raíz del chart, donde se encuentra el archivo `Chart.yaml` o especificando la ruta al directorio del chart en lugar del `.`.

Por defecto, el comando `helm template` usará los valores definidos en el archivo `values.yaml` por lo que no es necesario especificarlos en la línea de comandos, pero si deseas usar otros archivos de valores puedes hacerlo con la opción `-f`.

### 3. Instalar el chart

Para instalar el chart en tu clúster de Kubernetes, puedes usar el siguiente comando:

```bash
helm install my-nginx . -f values.yaml
```

Al igual que en el paso anterior, el comando anterior debe ejecutarse desde el directorio raíz del chart o especificando la ruta al directorio del chart en lugar del `.` y puedes usar la opción `-f` para especificar un archivo de valores diferente.

### 4. Verificar la instalación

Una vez que el chart se haya instalado correctamente, puedes verificar que el Pod de NGINX esté en estado `Running` con el siguiente comando:

```bash
kubectl get pods
```

---

## Personalización

Puedes personalizar la instalación del chart modificando los valores en el archivo `values.yaml`. Por ejemplo:

```yaml
replicaCount: 2
image:
  repository: nginx
  tag: 1.21.1
```

Una vez que hayas modificado los valores, puedes aplicar los cambios con el comando `helm upgrade`:

```bash
helm upgrade my-nginx . -f values.yaml
```

---

## Desinstalación

Para desinstalar el chart, puedes usar el comando `helm uninstall`:

```bash
helm uninstall my-nginx
```

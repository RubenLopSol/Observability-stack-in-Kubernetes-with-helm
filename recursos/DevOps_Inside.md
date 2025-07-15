# DevOps Inside: observabilidad desde dentro

Instrucciones.

> Usa los charts oficiales de Helm para desplegar: Grafana, Loki, Tempo y Mimir. Puedes encontrarlos en https://grafana.github.io/helm-charts.

> Todo debe estar dentro del clúster.

> Configura en modo monolítico. Más simple, sin dependencias externas.

> Asegúrate de que todo se ve bien desde Grafana: logs, métricas y trazas.

---

## Helm-charts Grafana:

https://github.com/grafana/helm-charts/tree/main/charts

- Grafana: https://github.com/grafana/helm-charts/tree/main/charts/grafana
- Loki: https://github.com/grafana/helm-charts/tree/main/charts/loki
- Mimir: https://github.com/grafana/mimir
- Tempo: https://github.com/grafana/helm-charts/tree/main/charts/tempo
- Alloy: https://github.com/grafana/alloy/tree/main/operations/helm/charts/alloy

---

## Estructura del repositorio

```bash
.
├── ansible/                # Playbooks de configuración
├── terraform/              # Módulos y configuraciones de IaC
├── k8s/                    # Manifiestos Kubernetes (Helm/Kustomize)
├── .github/workflows/      # Pipelines de CI/CD
├── scripts/                # Utilidades y automatizaciones
└── README.md

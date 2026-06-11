# Домашнее задание: Сетевая политика в Kubernetes (Calico)

## Выполнил - Машаев Роман

**Цель:**  
Настроить сетевую политику (Network Policy) для изоляции трафика между подами `frontend`, `backend` и `cache` в namespace `App`.  
Разрешить только цепочку `frontend → backend → cache`, все остальные подключения запретить.

## Предварительные требования

- Кластер Kubernetes с установленным сетевым плагином **Calico**.
- Утилита `kubectl`.
- Базовые знания Kubernetes.

## Файлы манифестов

Все манифесты лежат в папке `manifests/`:

- [`namespace.yaml`](./manifests/namespace.yaml) – создание namespace `App`
- [`deployments.yaml`](./manifests/deployments.yaml) – deployment'ы и сервисы для frontend, backend, cache
- [`policies.yaml`](./manifests/policies.yaml) – сетевые политики

## Выполнение задания (скриншоты выполнения)

1. **Поды и сервисы**  
   ![Поды и сервисы](k8s_9/screenshots/Screenshot_2026-06-11_15_28_21.png)

2. **Сетевые политики**  
   ![Сетевые политики](k8s_9/screenshots/Screenshot_2026-06-11_15_28_45.png)

3. **frontend → backend (разрешено)**  
   ![frontend->backend](k8s_9/screenshots/Screenshot_2026-06-11_15_30_39.png)

4. **backend → cache (разрешено)**  
   ![backend->cache](k8s_9/screenshots/Screenshot_2026-06-11_15_31_52.png)

5. **frontend → cache (заблокировано, завис)**  
   ![frontend->cache blocked](k8s_9/screenshots/Screenshot_2026-06-11_15_33_15.png)

6. **Доступ из namespace default (заблокирован,завис)**  
   ![from default blocked](k8s_9/screenshots/Screenshot_2026-06-11_15_34_46.png)

7. **cache → backend (заблокировано,завис)**  
   ![cache->backend blocked](k8s_9/screenshots/Screenshot_2026-06-11_15_38_25.png)

8. **backend → frontend (заблокировано, завис)**  
   ![backend->frontend blocked](k8s_9/screenshots/Screenshot_2026-06-11_15_40_33.png)




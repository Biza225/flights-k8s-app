# flights-k8s-app

Окей, тримай `README.md` для репозиторію `flights-k8s-app` 👇

```markdown
# ✈Flights K8s App

Веб-додаток на Flask, що працює в середовищі Kubernetes з базою даних PostgreSQL.  
Додаток дозволяє отримувати список авіарейсів у форматі JSON.

## Технології

- Python 3.10 + Flask
- PostgreSQL
- Docker
- Kubernetes (Minikube)
- Adminer (для перегляду БД)

---

## Структура проєкту

```
.
├── app.py
├── Dockerfile
├── app-deployment.yaml
├── db-deployment.yaml
├── db-service.yaml
├── app-service.yaml
└── README.md
```

---

## 🚀 Запуск у Minikube

1. **Запусти Minikube**
   ```bash
   minikube start
   ```

2. **Збілди Docker-образ всередині Minikube**
   ```bash
   eval $(minikube docker-env)
   docker build -t my-app-image .
   ```

3. **Застосуй Kubernetes-маніфести**
   ```bash
   kubectl apply -f db-deployment.yaml
   kubectl apply -f db-service.yaml
   kubectl apply -f app-deployment.yaml
   kubectl apply -f app-service.yaml
   ```

4. **Запусти Adminer**
   ```bash
   kubectl apply -f adminer-deployment.yaml
   kubectl apply -f adminer-service.yaml
   ```

5. **Відкрий у браузері**
   ```bash
   minikube service my-app
   minikube service adminer
   ```

---

## Структура таблиці в базі

```sql
CREATE TABLE flights (
    id SERIAL PRIMARY KEY,
    departure VARCHAR(100),
    arrival VARCHAR(100),
    departureDateTime TIMESTAMP,
    arrivalDateTime TIMESTAMP,
    price INTEGER,
    flightNumber VARCHAR(10),
    creationDate TIMESTAMP
);
```

---

## 🔗 Routes

- `GET /flights` — список усіх рейсів

---

## Приклад відповіді API

```json
[
  {
    "id": 1,
    "departure": "Kyiv",
    "arrival": "London",
    "departureDateTime": "2024-12-02T09:08:53.275942141",
    "arrivalDateTime": "2024-12-02T12:08:53.275967129",
    "price": 200,
    "flightNumber": "KL123",
    "creationDate": "2024-12-02T09:08:53.275998229"
  }
]
```

---

##Автор

biza — практична робота з Kubernetes + Docker + Flask + PostgreSQL

---

## Ліцензія

Вільне використання для навчання.
```

Можеш додати цей файл як звичайно:
```bash
git add README.md
git commit -m "Add README"
git push
```

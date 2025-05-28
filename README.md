# 📚 API de Reservas de Salas

Esta API permite o gerenciamento de reservas de salas para turmas escolares. Através dela, é possível listar, criar e consultar reservas específicas.

## ⚙ Como Rodar

```bash
python -m venv venv
source venv/Scripts/activate
pip install -r requirements.txt
docker build -t reservations
docker run -d -p 5002:5002 --name reservations reservations -d
```

## 🛠️ Endpoints

---

### 🔍 GET `/reservas`

Retorna a lista de todas as reservas cadastradas.

#### ✅ Exemplo de resposta:

```json
[
  {
    "id": 1,
    "sala": "Laboratório 3",
    "data": "25/05/2025",
    "hora_inicio": "14:00",
    "hora_fim": "16:00",
    "turma": {
      "id": 1,
      "nome": "9º Ano B",
      "turno": "Tarde",
      "professor": {
        "id": 2,
        "nome": "Ana Paula",
        "disciplina": "Física"
      },
      "alunos": []
    }
  }
]
```

---

### ➕ POST `/reservas`

Cria uma nova reserva de sala.

#### 📥 Corpo da requisição (JSON):

```json
{
  "turma_id": 1,
  "sala": "Laboratório 3",
  "data": "25/05/2025",
  "hora_inicio": "14:00",
  "hora_fim": "16:00"
}
```

#### ✅ Exemplo de resposta (JSON):

```json
{
  "mensagem": "Reserva criada com sucesso",
  "reserva": {
    "id": 2,
    "sala": "Laboratório 3",
    "data": "30/05/2025",
    "hora_inicio": "14:00",
    "hora_fim": "16:00",
    "turma": {
      "id": 1,
      "nome": "9º Ano B",
      "turno": "Tarde",
      "professor_id": 2,
      "professor": {
        "id": 2,
        "nome": "Ana Paula",
        "disciplina": "Física"
      },
      "alunos": []
    }
  }
}
```

---

### 🔎 GET `/reservas/<id>`

Retorna os detalhes de uma reserva específica pelo seu ID.

#### 🔗 Parâmetros de rota:

* `id` *(integer)*: ID da reserva a ser consultada.

#### ✅ Exemplo de resposta:

```json
{
  "id": 2,
  "sala": "Laboratório 3",
  "data": "30/05/2025",
  "hora_inicio": "14:00",
  "hora_fim": "16:00",
  "turma": {
    "id": 1,
    "nome": "9º Ano B",
    "turno": "Tarde",
    "professor_id": 2,
    "professor": {
      "id": 2,
      "nome": "Ana Paula",
      "disciplina": "Física"
    },
    "alunos": []
  }
}
```

# API Roadmap - Endpoints, Usage, and Examples

Segue a lista de endpoints agrupados por contexto, incluindo exemplos de requisição e resposta para cada um. Endpoints compartilhados estão agrupados no contexto "Compartilhado".

---

## Contexto: Compartilhado

### 1. GET /api/batidas  
- Páginas: index.html, sorteios.html  
- Descrição: Retorna a lista de entradas validadas ("batidas")  
- Exemplo de requisição:  
  ```
  GET /api/batidas
  ```  
- Exemplo de resposta:
  ```json
  [
    {
      "id": 1,
      "fantasyName": "Braga Araújo",
      "companyName": "Comercio de Insumos",
      "invoiceNumber": "9321",
      "unit": "Sete Lagoas",
      "cityState": "Pirapora Nossa/MG",
      "hitTime": "16:32",
      "delinquent": false,
      "cnpj": "07634924...",
      "contact": "(32) 9 9563-9130"
    }
  ]
  ```

### 2. GET /api/possibilidades  
- Páginas: index.html, sorteios.html  
- Descrição: Retorna a lista de possibilidades disponíveis  
- Exemplo de requisição:  
  ```
  GET /api/possibilidades
  ```  
- Exemplo de resposta:
  ```json
  [
    {
      "id": 101,
      "fantasyName": "Agrosul Agricola",
      "companyName": "Agrosul Agricola LTDA",
      "invoiceNumber": "0321",
      "unit": "Petrolina",
      "cityState": "Rio Grande do Sul/RS",
      "hitTime": "16:32",
      "delinquent": false,
      "cnpj": "07634924...",
      "contact": "(19) 9 9563-9130"
    }
  ]
  ```

### 3. GET /api/numeros-sorteados  
- Páginas: index.html, sorteios.html  
- Descrição: Retorna os números sorteados  
- Exemplo de requisição:  
  ```
  GET /api/numeros-sorteados
  ```  
- Exemplo de resposta:
  ```json
  {
    "drawnNumbers": [4, 3, 2, 1]
  }
  ```

---

## Contexto: Sessão ao Vivo (index.html)

### 4. GET /api/live-session  
- Descrição: Retorna informações da sessão atual (data, usuário, etc.)  
- Exemplo de requisição:  
  ```
  GET /api/live-session
  ```  
- Exemplo de resposta:
  ```json
  {
    "date": "2025-04-03",
    "user": "Guido Possi",
    "sessionStatus": "active"
  }
  ```

### 5. POST /api/sorteios/finish  
- Descrição: Marca a sessão TV ou sorteio específico como finalizado  
- Exemplo de requisição:  
  ```
  POST /api/sorteios/finish
  Content-Type: application/json

  {
    "sessionId": "12345"
  }
  ```  
- Exemplo de resposta:
  ```json
  {
    "success": true,
    "message": "Sorteio finalizado com sucesso."
  }
  ```

---

## Contexto: Audiência (audiencia.html)

### 6. GET /api/audience  
- Descrição: Retorna estatísticas da audiência do dia  
- Exemplo de requisição:  
  ```
  GET /api/audience
  ```  
- Exemplo de resposta:
  ```json
  {
    "totalEntries": 120,
    "exited": 37,
    "onlineNow": 83
  }
  ```

### 7. GET /api/chart-data  
- Descrição: Retorna dados para o gráfico de audiência  
- Exemplo de requisição:  
  ```
  GET /api/chart-data
  ```  
- Exemplo de resposta:
  ```json
  {
    "labels": ["1 month", "6 months", "1 year", "2 years", "Overall"],
    "data": [150, 180, 200, 170, 190]
  }
  ```

---

## Contexto: Edição de Imagens (editar-imagens.html)

### 8. GET /api/background-images  
- Descrição: Retorna URLs das imagens de fundo atuais  
- Exemplo de requisição:  
  ```
  GET /api/background-images
  ```  
- Exemplo de resposta:
  ```json
  {
    "tvNeutral": "https://example.com/images/tv-neutral.jpg",
    "tvDrawNumbers": "https://example.com/images/tv-draw-numbers.jpg",
    "tvWinner": "https://example.com/images/tv-winner.jpg",
    "tvRoulette": "https://example.com/images/tv-roulette.jpg"
  }
  ```

### 9. POST /api/background-images  
- Descrição: Faz upload/atualiza imagens de fundo  
- Exemplo de requisição:  
  ```
  POST /api/background-images
  Content-Type: multipart/form-data

  (form-data com arquivo de imagem)
  ```  
- Exemplo de resposta:
  ```json
  {
    "success": true,
    "message": "Imagem atualizada com sucesso."
  }
  ```

---

## Contexto: Fotos e Comentários (fotos-comentarios.html)

### 10. POST /api/photos  
- Descrição: Faz upload de foto com metadados  
- Exemplo de requisição:  
  ```
  POST /api/photos
  Content-Type: multipart/form-data

  (form-data com arquivo de imagem e campos: names, city, state, client)
  ```  
- Exemplo de resposta:
  ```json
  {
    "success": true,
    "photoId": 123,
    "message": "Foto enviada com sucesso."
  }
  ```

### 11. GET /api/photos  
- Descrição: Retorna lista de fotos do dia  
- Exemplo de requisição:  
  ```
  GET /api/photos
  ```  
- Exemplo de resposta:
  ```json
  [
    {
      "id": 123,
      "url": "https://example.com/photos/photo1.jpg",
      "names": "João, Maria",
      "city": "São Paulo",
      "state": "SP",
      "client": "Revenda X"
    }
  ]
  ```

### 12. POST /api/comments  
- Descrição: Envia novo comentário  
- Exemplo de requisição:  
  ```
  POST /api/comments
  Content-Type: application/json

  {
    "text": "Ótimo evento!",
    "author": "José da Silva"
  }
  ```  
- Exemplo de resposta:
  ```json
  {
    "success": true,
    "commentId": 456,
    "message": "Comentário enviado com sucesso."
  }
  ```

### 13. GET /api/comments  
- Descrição: Retorna lista atual de comentários  
- Exemplo de requisição:  
  ```
  GET /api/comments
  ```  
- Exemplo de resposta:
  ```json
  [
    {
      "id": 456,
      "text": "Ótimo evento!",
      "author": "José da Silva"
    }
  ]
  ```

---

## Contexto: Palpite Premiado (palpite-premiado.html)

### 14. GET /api/game-result  
- Descrição: Retorna resultado do jogo (placar, times)  
- Exemplo de requisição:  
  ```
  GET /api/game-result
  ```  
- Exemplo de resposta:
  ```json
  {
    "date": "2025-03-28",
    "teamA": "Corinthians",
    "scoreA": 4,
    "teamB": "Palmeiras",
    "scoreB": 1
  }
  ```

### 15. GET /api/palpites/correct  
- Descrição: Retorna lista de palpites corretos  
- Exemplo de requisição:  
  ```
  GET /api/palpites/correct
  ```  
- Exemplo de resposta:
  ```json
  [
    {
      "id": 1,
      "fantasyName": "Braga Araújo",
      "companyName": "Comercio de Insumos",
      "guess": "Corinthians 4 x 1 Palmeiras",
      "unit": "Sete Lagoas",
      "cityState": "Pirapora Nossa/MG",
      "registrationTime": "16:32",
      "delinquent": false,
      "cnpj": "07634924...",
      "contact": "(32) 9 9563-9130"
    }
  ]
  ```

### 16. GET /api/palpites/wrong  
- Descrição: Retorna lista de palpites errados  
- Exemplo de requisição:  
  ```
  GET /api/palpites/wrong
  ```  
- Exemplo de resposta:
  ```json
  [
    {
      "id": 2,
      "fantasyName": "Casa da Lavoura",
      "companyName": "Casa da Lavoura de Campos",
      "guess": "Corinthians 2 x 3 Palmeiras",
      "unit": "Sete Lagoas",
      "cityState": "Rio Grande do Sul/RS",
      "hitTime": "16:32",
      "delinquent": true,
      "cnpj": "07634924...",
      "contact": "(19) 9 9563-9130"
    }
  ]
  ```

### 17. POST /api/game-result  
- Descrição: Atualiza resultado do jogo (opcional)  
- Exemplo de requisição:  
  ```
  POST /api/game-result
  Content-Type: application/json

  {
    "date": "2025-03-28",
    "teamA": "Corinthians",
    "scoreA": 4,
    "teamB": "Palmeiras",
    "scoreB": 1
  }
  ```  
- Exemplo de resposta:
  ```json
  {
    "success": true,
    "message": "Resultado do jogo atualizado."
  }
  ```

### 18. GET /api/palpites/modal  
- Descrição: Retorna dados detalhados para modal "Palpite Premiado"  
- Exemplo de requisição:  
  ```
  GET /api/palpites/modal
  ```  
- Exemplo de resposta:
  ```json
  {
    "winners": [
      {
        "name": "Braga Araújo",
        "location": "Pirapora Nossa/MG",
        "unit": "Sete Lagoas"
      },
      {
        "name": "Agro Revenda LTDA",
        "location": "São Paulo-SP",
        "unit": "Paulínia"
      }
    ],
    "game": "Corinthians 4 x 1 Palmeiras",
    "date": "2025-04-03"
  }
  ```

---

## Contexto: Premiações (premiacoes.html)

### 19. GET /api/awards?year=YYYY  
- Descrição: Retorna premiações filtradas por ano  
- Exemplo de requisição:  
  ```
  GET /api/awards?year=2025
  ```  
- Exemplo de resposta:
  ```json
  [
    {
      "date": "2025-03-27",
      "fantasyName": "Braga Araújo",
      "companyName": "Comercio de Insumos",
      "award": "Alexa",
      "invoiceNumber": "9321",
      "unit": "Sete Lagoas",
      "cityState": "Pirapora Nossa/MG",
      "hitTime": "16:32",
      "delinquent": false,
      "cnpj": "07634924..."
    }
  ]
  ```

### 20. POST /api/awards  
- Descrição: Insere ou atualiza informações de premiação (opcional)  
- Exemplo de requisição:  
  ```
  POST /api/awards
  Content-Type: application/json

  {
    "date": "2025-03-27",
    "fantasyName": "Braga Araújo",
    "companyName": "Comercio de Insumos",
    "award": "Alexa",
    "invoiceNumber": "9321",
    "unit": "Sete Lagoas",
    "cityState": "Pirapora Nossa/MG",
    "hitTime": "16:32",
    "delinquent": false,
    "cnpj": "07634924..."
  }
  ```  
- Exemplo de resposta:
  ```json
  {
    "success": true,
    "message": "Premiação atualizada com sucesso."
  }
  ```

---

## Contexto: Prêmio Extra (premio-bola-maior.html)

### 21. GET /api/extra-prize  
- Descrição: Retorna detalhes do "Prêmio Extra"  
- Exemplo de requisição:  
  ```
  GET /api/extra-prize
  ```  
- Exemplo de resposta:
  ```json
  {
    "batidas": [
      {
        "name": "Braga Araújo",
        "company": "Comercio de Insumos",
        "extra": 0,
        "centena": 0,
        "milhar": 0,
        "invoiceNumber": "9321",
        "unit": "Sete Lagoas",
        "cityState": "Pirapora Nossa/MG",
        "hitTime": "16:32",
        "delinquent": false
      }
    ]
  }
  ```

### 22. POST /api/extra-prize  
- Descrição: Atualiza detalhes do prêmio extra (opcional)  
- Exemplo de requisição:  
  ```
  POST /api/extra-prize
  Content-Type: application/json

  {
    "batidas": [
      {
        "name": "Braga Araújo",
        "extra": 1,
        "centena": 2,
        "milhar": 0
      }
    ]
  }
  ```  
- Exemplo de resposta:
  ```json
  {
    "success": true,
    "message": "Prêmio extra atualizado."
  }
  ```

---

## Contexto: Sorteios (sorteios.html)

### 23. GET /api/sorteios/settings  
- Descrição: Retorna configurações atuais da loteria  
- Exemplo de requisição:  
  ```
  GET /api/sorteios/settings
  ```  
- Exemplo de resposta:
  ```json
  {
    "listTypes": ["GRV", "GRR", "Festão"],
    "selectedTypes": ["GRV"],
    "rounds": 1,
    "ballsQuantity": 90
  }
  ```

### 24. POST /api/sorteios/config  
- Descrição: Envia configurações atualizadas da loteria  
- Exemplo de requisição:  
  ```
  POST /api/sorteios/config
  Content-Type: application/json

  {
    "selectedTypes": ["GRV", "Festão"],
    "rounds": 2,
    "ballsQuantity": 90
  }
  ```  
- Exemplo de resposta:
  ```json
  {
    "success": true,
    "message": "Configurações atualizadas."
  }
  ```

### 25. POST /api/sorteios/finish-round  
- Descrição: Marca a rodada atual como finalizada  
- Exemplo de requisição:  
  ```
  POST /api/sorteios/finish-round
  Content-Type: application/json

  {
    "round": 1
  }
  ```  
- Exemplo de resposta:
  ```json
  {
    "success": true,
    "message": "Rodada finalizada."
  }
  ```

### 26. GET /api/sorteios/batidas  
- Descrição: Retorna dados de batidas para a rodada atual  
- Exemplo de requisição:  
  ```
  GET /api/sorteios/batidas
  ```  
- Exemplo de resposta:
  ```json
  [
    {
      "id": 1,
      "fantasyName": "Braga Araújo",
      "companyName": "Comercio de Insumos",
      "carnet": "932102",
      "unit": "Sete Lagoas",
      "cityState": "Pirapora Nossa/MG",
      "hitTime": "16:32",
      "delinquent": false,
      "cnpj": "07634924...",
      "contact": "(32) 9 9563-9130"
    }
  ]
  ```

### 27. GET /api/sorteios/possibilidades  
- Descrição: Retorna possibilidades para a rodada atual  
- Exemplo de requisição:  
  ```
  GET /api/sorteios/possibilidades
  ```  
- Exemplo de resposta:
  ```json
  [
    {
      "id": 101,
      "fantasyName": "Agrosul Agrovicola",
      "companyName": "Agrosul Agrovicola LTDA",
      "invoiceNumber": "032123",
      "unit": "Petrolina",
      "cityState": "Rio Grande do Sul/RS",
      "hitTime": "16:32",
      "delinquent": false,
      "cnpj": "07634924...",
      "contact": "(19) 9 9563-9130"
    }
  ]
  ```

### 28. GET /api/sorteios/ticker (opcional)  
- Descrição: Fornece atualizações ao vivo via polling ou WebSocket  
- Exemplo de requisição:  
  ```
  GET /api/sorteios/ticker
  ```  
- Exemplo de resposta:
  ```json
  {
    "latestNumber": 42,
    "round": 1,
    "timestamp": "2025-04-03T16:32:00Z"
  }
  ```

---

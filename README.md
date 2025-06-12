Instruções para executar:
Crie/atualize o ambiente virtual: python -m venv venv
Ative o ambiente virtual:
Windows: venv\Scripts\activate
Linux/Mac: source venv/bin/activate
Instale as dependências: pip install -r requirements.txt
Execute a aplicação: python app.py
Como usar a autenticação:
Registrar um usuário:
bash



curl -X POST http://localhost:5000/register -H "Content-Type: application/json" -d '{"name":"João Silva","email":"joao@example.com","password":"sua-senha"}'
Fazer login e obter token:
bash



curl -X POST http://localhost:5000/login -H "Content-Type: application/json" -d '{"email":"joao@example.com","password":"sua-senha"}'
O retorno será um token JWT, por exemplo: {"token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..."}.
Acessar endpoints protegidos: Use o token no header Authorization com o prefixo Bearer:
bash



curl -X GET http://localhost:5000/users -H "Authorization: Bearer seu-token-aqui"
Observações:
Altere app.config['SECRET_KEY'] para uma chave secreta segura em produção.
O token expira em 24 horas (configurável no parâmetro exp do jwt.encode).
Todos os endpoints, exceto /register e /login, agora exigem um token válido.
O banco de dados continua usando SQLite para simplicidade, mas pode ser alterado para outros bancos suportados pelo SQLAlchemy.
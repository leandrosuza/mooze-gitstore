# 🍔 Sistema de Hamburgueria - BurgerMaster

Sistema completo para operação de hamburgueria com gestão de pedidos, mesas, estoque e relatórios.

## 🚀 Funcionalidades Implementadas

### ✅ Gestão de Produtos
- Cadastro de produtos com categorias
- Upload de imagens
- Controle de preços e descrições
- Sistema de ativação/desativação

### ✅ Sistema de Mesas
- Gerenciamento de mesas com QR codes únicos
- Controle de ocupação e reservas
- Timer de permanência na mesa
- Status em tempo real

### ✅ Cardápio Mobile
- Interface responsiva para clientes
- Navegação por categorias
- Carrinho de compras
- Sistema de pedidos com confirmação

### ✅ Gestão de Pedidos
- Visualização em tempo real
- Filtros avançados (status, mesa, data, categoria)
- Numeração sequencial automática
- Notificações de novos pedidos
- Controle de status (pendente, preparando, pronto, entregue)

### ✅ Controle de Estoque
- Cadastro de itens de estoque
- Movimentações (entrada, saída, ajuste)
- Controle de validade
- Alertas de estoque baixo

### ✅ Sistema de Pagamentos
- Múltiplos métodos (Na Recepção, PIX, Cartão)
- Integração com ocupação de mesas
- Confirmação personalizada

## 🛠️ Tecnologias

### Backend
- **Node.js** com Express
- **TypeScript** para tipagem
- **SQLite3** como banco de dados
- **Zod** para validação de schemas
- **Multer** para upload de arquivos
- **QRCode** para geração de códigos QR

### Frontend
- **HTML5** semântico
- **Tailwind CSS** para estilização
- **JavaScript ES6+** modular
- **Font Awesome** para ícones
- **SPA Router** customizado

## 📁 Estrutura do Projeto

```
Hamburgueria/
├── backend/                 # API e lógica de negócio
│   ├── src/
│   │   ├── modules/        # Módulos de negócio
│   │   │   ├── products.ts
│   │   │   ├── categories.ts
│   │   │   ├── orders.ts
│   │   │   ├── tables.ts
│   │   │   ├── stock.ts
│   │   │   └── uploads.ts
│   │   ├── server.ts       # Servidor principal
│   │   └── db.ts          # Configuração do banco
│   └── uploads/           # Arquivos de upload
├── frontend/              # Interface do usuário
│   ├── screens/          # Telas do sistema
│   │   ├── dashboard.html
│   │   ├── cardapio.html
│   │   ├── pedidos.html
│   │   ├── mesas.html
│   │   ├── estoque.html
│   │   └── cardapio-mobile.html
│   ├── src/
│   │   ├── css/          # Estilos específicos
│   │   └── js/           # Lógica das telas
│   └── main.js           # Router SPA
└── README.md
```

## 🚀 Como Executar

### Pré-requisitos
- Node.js 18+ instalado
- Navegador moderno

### Instalação
```bash
# Instalar dependências do backend
cd backend
npm install

# Instalar dependências do frontend (se necessário)
cd ../frontend
npm install
```

### Execução
```bash
# Iniciar o servidor backend
cd backend
npm run dev

# O sistema estará disponível em:
# - Admin: http://localhost:3000
# - Mobile: http://localhost:3000/cardapio?mesa=1
```

## 📱 Acesso Mobile

Para acessar o cardápio mobile, escaneie o QR code de uma mesa ou acesse:
```
http://[IP_DO_SERVIDOR]:3000/cardapio?mesa=[NUMERO_DA_MESA]
```

## 🔧 Configuração de Rede

Para acesso externo (celulares, outros dispositivos):

1. Descubra o IP da máquina:
```bash
# Windows
ipconfig

# Linux/Mac
ifconfig
```

2. Acesse pelo IP:
```
http://[SEU_IP]:3000
```

3. Configure firewall se necessário (Windows):
- Abra "Firewall do Windows Defender"
- Adicione regra de entrada para porta 3000

## 👥 Funcionalidades para Funcionários
  
### Login de Funcionários
- Endpoints: `POST /api/employees/login`, `POST /api/employees/logout`, `POST /api/employees/logout-all`
- Rota web: `/login-funcionario`
- Sessão persistente por 24h (armazenada no dispositivo)
- Status dinâmico: ativo ao logar, inativo ao deslogar
  
### Pedidos por Funcionários
- Rota web: `/pedidos-funcionario`
- Campos adicionais no pedido: `employeeId`, `employeeName`
- Método de pagamento para funcionários: sempre `reception`
- Fluxo: login → escolher mesa → montar pedido → confirmar
  
### Logout Automático
- Na inicialização do servidor, todos os funcionários são deslogados automaticamente
- Função: `logoutAllEmployees()`
- Endpoint administrativo: `POST /api/employees/logout-all`

## 📊 Funcionalidades por Tela

### Dashboard
- Visão geral do sistema
- Estatísticas de vendas
- Alertas e notificações

### Cardápio (Admin)
- Gerenciar produtos e categorias
- Upload de imagens
- Controle de preços
- Ativação/desativação

### Pedidos
- Lista de pedidos em tempo real
- Filtros avançados
- Controle de status
- Notificações automáticas

### Mesas
- Gerenciar mesas
- Gerar QR codes
- Controle de ocupação
- Timer de permanência

### Estoque
- Cadastro de itens
- Movimentações
- Controle de validade
- Alertas de estoque

### Cardápio Mobile
- Interface para clientes
- Navegação por categorias
- Carrinho de compras
- Sistema de pedidos

## 🔄 Fluxo de Trabalho

1. **Configuração Inicial**
   - Cadastrar produtos no cardápio
   - Configurar mesas e gerar QR codes
   - Cadastrar itens de estoque

2. **Operação Diária**
   - Clientes escaneiam QR code da mesa
   - Fazem pedidos pelo mobile
   - Pedidos aparecem na tela de Pedidos
   - Cozinha prepara e atualiza status
   - Mesa é ocupada automaticamente

3. **Gestão**
   - Monitorar pedidos em tempo real
   - Controlar estoque
   - Gerar relatórios

## 🎯 Próximas Funcionalidades

- [ ] Sistema de relatórios avançados
- [ ] Integração com impressora térmica
- [ ] Sistema de promoções
- [ ] Cadastro de clientes
- [ ] Integração WhatsApp
- [ ] Sistema de fidelidade

## 🐛 Solução de Problemas

### Problemas Comuns

1. **Erro de conexão mobile**
   - Verifique o IP do servidor
   - Configure firewall
   - Teste conectividade de rede

2. **Imagens não carregam**
   - Verifique pasta uploads/
   - Permissões de escrita
   - Tamanho dos arquivos

3. **Pedidos não aparecem**
   - Verifique console do navegador
   - Teste API endpoints
   - Verifique banco de dados

## 📝 Logs e Debug

Para debug, verifique:
- Console do navegador (F12)
- Logs do servidor backend
- Banco de dados SQLite

## 🤝 Contribuição

Para contribuir com o projeto:
1. Faça fork do repositório
2. Crie uma branch para sua feature
3. Commit suas mudanças
4. Abra um Pull Request

## 📄 Licença

Este projeto é de uso interno e proprietário.

---

**Desenvolvido com ❤️ para otimizar operações de hamburgueria**




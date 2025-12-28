# 🧪 Guia de Teste - Catly Barbearia App

## 🌐 Acesso à Aplicação

**URL Local**: http://localhost:3001

O servidor está rodando e pronto para uso!

---

## 📍 Teste 1: Geolocalização (PRINCIPAL)

### Objetivo
Verificar se a aplicação identifica sua localização corretamente.

### Passos
1. Abra http://localhost:3001 no navegador
2. O navegador vai pedir permissão para acessar sua localização
3. **Clique em "Permitir"**
4. Aguarde alguns segundos
5. No topo da página, você deve ver:
   - ✅ **Com API Gemini**: "Bairro, Cidade, Província" (ex: "Polana Cimento, Maputo, Cidade de Maputo")
   - ✅ **Sem API**: Nome da cidade via OpenStreetMap

### Resultado Esperado
- ✅ Localização identificada e exibida
- ✅ Ícone de localização visível
- ✅ Pode clicar no ícone para atualizar

### Solução de Problemas
- ❌ **"Buscando..."** não muda: 
  - Verifique se permitiu a localização
  - Clique no ícone de localização para tentar novamente
  - Abra o Console (F12) e veja se há erros

- ❌ **"São Paulo, SP"**: 
  - Localização negada ou erro
  - Isso é o fallback padrão (normal se negar permissão)

---

## 🤖 Teste 2: Dicas de IA

### Objetivo
Verificar se a IA Gemini está respondendo com dicas de estilo.

### Passos
1. Na página inicial, clique em qualquer **barbearia**
2. Role até a seção **"Catly AI • Consultoria"** (card azul)
3. Clique em qualquer **serviço** (ex: "Corte Degradê")
4. Aguarde 2-3 segundos
5. Deve aparecer uma dica personalizada

### Resultado Esperado
- ✅ Texto "Analisando estilo..." aparece
- ✅ Depois de alguns segundos, aparece uma dica em português
- ✅ Exemplo: "Para o corte degradê, mantenha os lados bem definidos..."

### Solução de Problemas
- ❌ **Mensagem padrão**: 
  - API key pode estar incorreta
  - Verifique o arquivo `.env.local`
  - Abra o Console (F12) para ver erros

---

## 📅 Teste 3: Fluxo de Agendamento

### Objetivo
Testar o fluxo completo de reserva.

### Passos
1. Clique em **"RESERVAR"** em qualquer barbearia
2. **Passo 1**: Selecione um ou mais serviços → Clique "Continuar"
3. **Passo 2**: Escolha um profissional → Clique "Continuar"
4. **Passo 3**: Selecione data e horário → Clique "Continuar"
5. **Passo 4**: Revise e clique "Confirmar Agendamento"
6. Deve aparecer mensagem de sucesso

### Resultado Esperado
- ✅ Navegação suave entre etapas
- ✅ Indicador de progresso funcionando
- ✅ Botão "Voltar" funciona
- ✅ Confirmação exibida ao final

---

## 🎨 Teste 4: Interface e Animações

### Objetivo
Verificar se o design está correto e animações funcionam.

### Checklist Visual
- [ ] **Tema dark** aplicado (fundo escuro)
- [ ] **Ícones Material Symbols** carregados
- [ ] **Fonte Manrope** aplicada
- [ ] **Animações suaves** ao navegar
- [ ] **Cards com bordas arredondadas**
- [ ] **Efeitos hover** nos botões
- [ ] **Scrollbar personalizada** (se no desktop)

### Teste de Responsividade
1. Pressione **F12** para abrir DevTools
2. Clique no ícone de **dispositivo móvel** (Ctrl+Shift+M)
3. Teste em diferentes tamanhos:
   - iPhone SE (375px)
   - iPhone 12 Pro (390px)
   - iPad (768px)
   - Desktop (1920px)

---

## 🗺️ Teste 5: Navegação Completa

### Objetivo
Testar todas as rotas da aplicação.

### Rotas para Testar
1. **Home** (`/`) - Lista de barbearias ✅
2. **Detalhes** (`/barbershop/:id`) - Clique em uma barbearia ✅
3. **Agendamento** (`/booking/:id`) - Clique em "Reservar" ✅
4. **Perfil** (`/profile`) - Clique no avatar no topo ✅
5. **Mapa** (`/map`) - Clique em "Ver Mapa" (se disponível) ✅
6. **Agendamentos** (`/appointments`) - Via menu de navegação ✅

---

## 🔍 Teste 6: Console do Navegador

### Objetivo
Verificar se não há erros críticos.

### Passos
1. Pressione **F12** para abrir DevTools
2. Vá para a aba **Console**
3. Recarregue a página (F5)
4. Observe as mensagens

### Resultado Esperado
- ✅ Sem erros vermelhos críticos
- ⚠️ Avisos (warnings) amarelos são aceitáveis
- ℹ️ Mensagens informativas são normais

### Mensagens Normais
```
📍 Usando OpenStreetMap para geocodificação
⚠️ Gemini API Key não configurada (se não tiver API key)
```

### Erros a Investigar
```
❌ Failed to fetch
❌ API key invalid
❌ Network error
```

---

## 📊 Checklist Final

### Funcionalidades Core
- [ ] Aplicação carrega sem erros
- [ ] Localização é identificada
- [ ] Lista de barbearias aparece
- [ ] Busca funciona
- [ ] Filtros por categoria funcionam
- [ ] Favoritos podem ser marcados
- [ ] Navegação entre páginas funciona

### IA e API
- [ ] Dicas de IA aparecem ao clicar em serviços
- [ ] Geolocalização usa Gemini ou OpenStreetMap
- [ ] Sem erros de API no console

### UX/UI
- [ ] Design moderno e premium
- [ ] Animações suaves
- [ ] Tema dark aplicado
- [ ] Responsivo em mobile
- [ ] Ícones carregados

---

## 🚨 Problemas Comuns

### "Localização não identificada"
**Solução**: 
1. Verifique se permitiu acesso à localização
2. Tente em outro navegador
3. Verifique se o GPS está ativado (mobile)

### "Dicas de IA não aparecem"
**Solução**:
1. Verifique o arquivo `.env.local`
2. Confirme que a API key está correta
3. Verifique o console para erros de API

### "Página em branco"
**Solução**:
1. Abra o Console (F12)
2. Veja o erro específico
3. Recarregue a página (Ctrl+F5)

### "Estilos não aplicados"
**Solução**:
1. Verifique se `index.css` existe
2. Limpe o cache (Ctrl+Shift+Delete)
3. Recarregue com cache limpo (Ctrl+F5)

---

## 📞 Suporte

Se encontrar algum problema:
1. Abra o Console do navegador (F12)
2. Copie a mensagem de erro
3. Verifique os arquivos de documentação:
   - `RESUMO_CORRECOES.md`
   - `CHECKLIST.md`
   - `README.md`

---

**Boa sorte com os testes! 🚀**

A aplicação está 100% funcional e pronta para uso!

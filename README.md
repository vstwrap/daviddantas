Painel de Relatório de Lojas
Este é um aplicativo web completo para visualização e gerenciamento de dados de performance de lojas. Ele permite cadastrar lojas, registrar dados diários de vendas e analisar os indicadores através de dashboards interativos.

Funcionalidades
Dashboard Geral: Visão rápida dos KPIs mais importantes (Faturamento, Ticket Médio, Taxa de Conversão) com comparações mensais.

Análise Detalhada: Gráficos e tabelas para analisar a performance em períodos personalizados.

Análise Comparativa: Compare a performance do mês atual com o mês anterior.

Cadastro e Gestão:

Adicione, edite e remova lojas.

Adicione, edite e remova registros diários de vendas.

Exportação para Excel: Exporte os dados das principais tabelas para arquivos .xlsx com um clique.

Persistência de Dados: Utiliza o Firebase Firestore para armazenar todos os dados de forma segura na nuvem.

Tecnologias Utilizadas
HTML5

Tailwind CSS para estilização.

Chart.js para a criação de gráficos dinâmicos.

SheetJS (xlsx.js) para a exportação de dados para o formato Excel.

Firebase para autenticação e banco de dados em tempo real (Firestore).

Como Configurar e Executar
Siga estes 5 passos para configurar o projeto:

Passo 1: Crie um Projeto no Firebase
Acesse o console do Firebase.

Clique em "Adicionar projeto" e siga as instruções para criar um novo projeto.

Passo 2: Adicione um Aplicativo Web e Obtenha a Configuração
Dentro do seu projeto Firebase, clique no ícone da Web (</>) para adicionar um novo aplicativo web.

Dê um apelido ao seu aplicativo (ex: "Painel de Lojas") e clique em "Registrar aplicativo".

O Firebase exibirá um objeto chamado firebaseConfig. Copie este objeto completo. Ele se parecerá com isto:

const firebaseConfig = {
  apiKey: "AIza...",
  authDomain: "seu-projeto.firebaseapp.com",
  projectId: "seu-projeto",
  storageBucket: "seu-projeto.appspot.com",
  messagingSenderId: "...",
  appId: "1:..."
};

Passo 3: Habilite a Autenticação e o Firestore
No menu do Firebase, vá para Authentication > Sign-in method.

Selecione "Anônimo" e ative-o.

Agora, vá para Firestore Database > Criar banco de dados.

Inicie em modo de produção e clique em "Avançar". Escolha a localização do servidor (ex: southamerica-east1).

Após a criação, vá para a aba "Regras" e cole o seguinte código, substituindo as regras existentes. Clique em "Publicar".

rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Permite que qualquer usuário autenticado (incluindo anônimo) leia e escreva
    // nos dados públicos do aplicativo.
    match /artifacts/{appId}/public/data/{collection}/{docId} {
      allow read, write: if request.auth != null;
    }
  }
}

Passo 4: Cole sua Configuração no index.html
Abra o arquivo index.html que você criou.

Procure pela linha const firebaseConfig =.

Substitua o objeto de exemplo pelo seu próprio objeto firebaseConfig que você copiou no Passo 2.

Passo 5: Execute o Aplicativo
Salve o arquivo index.html com suas alterações.

Abra o arquivo index.html diretamente em seu navegador (Google Chrome, Firefox, etc.).

O aplicativo irá carregar e se conectar automaticamente ao seu banco de dados Firebase. Você já pode começar a cadastrar lojas e registros!

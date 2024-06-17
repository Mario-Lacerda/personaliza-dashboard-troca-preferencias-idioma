

Desafio Dio - Personalizando Dashboard e Trocando as Preferências de Idioma


Descrevendo um exemplo prático de como podemos personalizar um dashboard e alterar as preferências de idioma. Vamos imaginar que estamos trabalhando com um dashboard de vendas que precisa ser adaptado para usuários de diferentes países.


Personalização do Dashboard

Layout e Tema:

Comece definindo um tema padrão que possa ser facilmente alterado. Por exemplo, crie variáveis CSS para cores e fontes que podem ser modificadas através de um menu de configurações.

Permita que os usuários escolham entre um layout claro e escuro.

Widgets e Componentes:

Ofereça a opção de adicionar, remover ou reorganizar widgets no dashboard, como gráficos de vendas, listas de tarefas e calendários.

Use uma biblioteca de arrastar e soltar para facilitar a personalização do layout pelos usuários.

Configurações de Exibição:

Permita que os usuários configurem o que é exibido em cada widget, como selecionar quais métricas de vendas querem acompanhar.
Troca de Idioma
Internacionalização (i18n):

Implemente uma biblioteca de i18n para gerenciar as traduções do seu dashboard.
Crie arquivos de recursos de idioma (por exemplo, en.json, pt.json, es.json) que contenham todas as strings traduzidas.

Localização (L10n):

Além das traduções, ajuste formatos de data, hora e moeda para corresponder ao local do usuário.
Considere diferenças culturais que podem influenciar a interface do usuário, como cores e ícones.

Seleção de Idioma:

Adicione um menu ou configuração onde os usuários possam selecionar seu idioma preferido.
Salve a preferência de idioma do usuário para que o dashboard carregue automaticamente com o idioma escolhido na próxima visita.

Atualização Dinâmica:

Use uma função para atualizar o texto exibido em tempo real quando o usuário altera o idioma.
Garanta que a mudança de idioma não afete o estado atual do dashboard, mantendo os dados e configurações do usuário intactos.

Aqui está um exemplo de código que demonstra a troca de idioma usando JavaScript:

// Objeto com traduções
const traducoes = {
  en: {
    sales: "Sales",
    tasks: "Tasks",
    settings: "Settings"
  },
  pt: {
    sales: "Vendas",
    tasks: "Tarefas",
    settings: "Configurações"
  }
};

// Função para alterar o idioma
function mudarIdioma(idioma) {
  document.getElementById('label-sales').textContent = traducoes[idioma].sales;
  document.getElementById('label-tasks').textContent = traducoes[idioma].tasks;
  document.getElementById('label-settings').textContent = traducoes[idioma].settings;
}

// Evento para detectar a mudança de idioma
document.getElementById('select-language').addEventListener('change', (event) => {
  mudarIdioma(event.target.value);
});
Este é apenas um exemplo simplificado. Em um projeto real, nós teríamos que lidar com mais strings e possivelmente usar uma biblioteca de i18n para facilitar o gerenciamento das traduções. Espero que este exemplo ajude a ilustrar como podemos começar a personalizar um dashboard e implementar a troca de idiomas.

Aqui estão exemplos práticos de como implementar a internacionalização em aplicações usando os frameworks React e Angular:

React
Para internacionalizar uma aplicação React, podemos usar a biblioteca react-intl, que faz parte do projeto FormatJS. Aqui está um exemplo simplificado de como podemos configurar e usar react-intl:

Instale a biblioteca react-intl:
npm install react-intl
Crie arquivos de mensagens para cada idioma:
// en.js
const en = {
  'app.greeting': 'Hello!',
  // outras strings de tradução...
};

// pt.js
const pt = {
  'app.greeting': 'Olá!',
  // outras strings de tradução...
};

export { en, pt };
Configure o IntlProvider e use o hook useIntl:
import { IntlProvider, useIntl } from 'react-intl';
import { en, pt } from './messages';

function App() {
  const messages = { en, pt };
  const locale = 'pt'; // ou 'en', dependendo da preferência do usuário

  return (
    <IntlProvider locale={locale} messages={messages[locale]}>
      <MyComponent />
    </IntlProvider>
  );
}

function MyComponent() {
  const intl = useIntl();
  return <p>{intl.formatMessage({ id: 'app.greeting' })}</p>;
}
Angular
Para internacionalizar uma aplicação Angular, podemos usar o recurso de internacionalização (i18n) integrado do Angular. Aqui está um exemplo de como podemos usar i18n no Angular:

Marque os textos que precisam ser traduzidos:
<!-- app.component.html -->
<h1 i18n="@@greeting">Olá!</h1>
Extraia os textos para um arquivo de tradução:
ng xi18n --output-path locale
Adicione as traduções no arquivo .xlf:
<trans-unit id="greeting" datatype="html">
  <source>Olá!</source>
  <target>Hello!</target>
</trans-unit>
Configure o build para cada idioma:
ng build --configuration=en
Use o serviço TranslateService para alternar idiomas:
import { TranslateService } from '@ngx-translate/core';

constructor(private translate: TranslateService) {
  translate.setDefaultLang('en');
}

switchLanguage(language: string) {
  this.translate.use(language);
}
Esses são exemplos básicos para começar a internacionalização com React e Angular. Para uma implementação mais detalhada, podemos consultar a documentação oficial ou tutoriais específicos para cada framework.


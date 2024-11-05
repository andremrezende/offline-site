# Site offline

Para possibilitar que um site funcione offline, é possível usar o Service Worker e a Cache Storage API. 
Isso permite que o conteúdo seja armazenado no cache do navegador para ser acessado sem conexão com a internet. 

## Testando o Projeto Offline
1. Inicie um servidor local para que o Service Worker funcione (exemplo: você pode usar a extensão do VS Code Live Server ou outro servidor local de sua preferência).
2. Acesse o site (localhost na porta configurada pelo seu servidor local).
3. Abra as DevTools do navegador (F12 no Chrome), vá até a aba Application > Service Workers e verifique se o Service Worker foi registrado.
4. Ative o modo Offline no navegador (em DevTools, vá para a aba Network e selecione Offline).
5. Recarregue a página para verificar se os arquivos estão sendo carregados do cache.

## Explicação do Funcionamento
* Instalação do Service Worker: Na primeira execução, o Service Worker é registrado e faz cache dos arquivos listados em urlsToCache.
* Interceptação de Requisições: Quando uma requisição é feita, o Service Worker tenta servir os arquivos do cache. Se eles não estiverem disponíveis no cache, ele faz uma requisição de rede.
* Atualização do Cache: Quando uma nova versão do Service Worker é instalada (alteração no CACHE_NAME), o cache antigo é limpo.
Esse é um exemplo básico, mas você pode expandir para incluir páginas adicionais e cache dinâmico para outros tipos de conteúdo.
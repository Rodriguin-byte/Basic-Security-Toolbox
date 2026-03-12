Security Tools Suite
Versão: 3.0
Python: 3.6 ou superior

AVISO LEGAL
Esta ferramenta é apenas para fins educacionais e testes de segurança autorizados.

O uso não autorizado desta ferramenta em sistemas que não possui ou sem permissão explícita é ilegal e antiético. O utilizador é o único responsável por garantir que tem permissão para testar os alvos.

Sobre o Projeto
O Security Tools Suite é uma ferramenta completa de testes de segurança desenvolvida em Python, que reúne diversas funcionalidades para análise e auditoria de websites e aplicações web. Foi criada como projeto de estudo para compreender melhor as vulnerabilidades comuns e técnicas de teste de penetração.

Funcionalidades
1. Port Scanner Profissional
Scan de portas TCP com múltiplas threads

Deteção de serviços em portas abertas

Configurável (portas, timeout, threads)

Resolução de domínios para IP

2. Directory Bruteforcer
Descoberta de diretórios e ficheiros

Suporte para múltiplas extensões (php, asp, txt, bak, etc.)

Multi-threading para maior velocidade

Deteção de redirecionamentos e acessos restritos

3. Subdomain Enumerator
Enumeração de subdomínios através de wordlist

Resolução DNS para confirmação

Verificação de serviços HTTP ativos

Wordlist abrangente de subdomínios comuns

4. XSS Vulnerability Scanner
Testes de Cross-Site Scripting (XSS)

Múltiplos payloads de teste

Análise de formulários automaticamente

Testes em parâmetros URL

5. SQL Injection Tester
Testes de injeção SQL (error-based, time-based)

Payloads para diferentes tipos de SQLi

Deteção de erros SQL em respostas

Testes de bypass de autenticação

6. Security Headers Analyzer
Análise de cabeçalhos de segurança

Verificação de: HSTS, CSP, X-Frame-Options, etc.

Pontuação de segurança

Recomendações para headers ausentes

7. WAF Detector
Identificação de Web Application Firewalls

Deteção por headers e cookies

Reconhecimento de: Cloudflare, AWS WAF, ModSecurity, F5, Sucuri, etc.

Testes com payloads maliciosos para confirmação

8. SSL/TLS Checker
Verificação de certificados SSL

Informações de emissor e validade

Dias restantes até expiração

Versão TLS e cipher em uso

Subject Alternative Names (SANs)

9. Web Crawler
Crawling automático de websites

Extração de títulos e informações de páginas

Limite configurável de páginas

Descoberta de links internos

10. Relatório Completo
Execução automática de todas as ferramentas

Relatório consolidado em JSON

Resumo executivo dos resultados

Ideal para auditorias rápidas

11. Configurações
Definição de target global

Configuração de User-Agent

Adição de cookies de sessão

Verificação de dependências

Instalação
Pré-requisitos
Python 3.6 ou superior

pip (gerenciador de pacotes Python)

Passos de Instalação
Clonar o repositório

bash
git clone https://github.com/seu-usuario/security-tools-suite.git
cd security-tools-suite
Instalar dependências

bash
pip install requests beautifulsoup4 urllib3
Executar a ferramenta

bash
python3 security_suite.py
Como Usar
Iniciar a ferramenta

bash
python3 security_suite.py
Confirmar o aviso legal

A ferramenta pedirá confirmação de que tem permissão para testar o alvo

Navegar pelo menu

Escolha uma opção de 0 a 11

Configure o target quando solicitado

Ajuste parâmetros conforme necessário

Analisar resultados

Resultados são mostrados em tempo real no terminal

Relatórios são guardados em formato JSON com timestamp

Use a opção 10 para um relatório completo

Exemplo de Uso Rápido
text
1. Escolha a opção 1 (Port Scanner)
2. Introduza o target (ex: exemplo.com)
3. Configure portas (ex: 1-1024)
4. Aguarde o scan
5. Veja as portas abertas encontradas
Estrutura dos Relatórios
Os relatórios são guardados em formato JSON com a seguinte estrutura:

json
{
    "tool": "nome_da_ferramenta",
    "target": "alvo_testado",
    "timestamp": "20240101_120000",
    "data": {
        "resultados_específicos": "valores"
    }
}
Dependências
requests - Requisições HTTP

beautifulsoup4 - Parsing de HTML (opcional para algumas funcionalidades)

urllib3 - Cliente HTTP com suporte a SSL

Funcionalidades por Ferramenta
Ferramenta	Descrição	Dependências
Port Scanner	Scan TCP multi-thread	socket
Directory Bruteforcer	Descoberta de diretórios	requests
Subdomain Enumerator	Enumeração de subdomínios	socket, requests
XSS Scanner	Testes de XSS	requests, bs4
SQL Tester	Testes de SQLi	requests
Security Headers	Análise de headers	requests
WAF Detector	Identificação de WAF	requests
SSL Checker	Verificação SSL	ssl, socket
Web Crawler	Crawling de sites	requests, bs4
Limitações e Considerações
Algumas funcionalidades requerem BeautifulSoup4 (instalação opcional)

O scanner não é tão rápido quanto ferramentas profissionais como Nmap

Wordlists são limitadas (para uso educacional)

Pode gerar falsos positivos em alguns casos

Personalização
Adicionar Wordlists Próprias
Pode modificar as wordlists nas funções correspondentes:

directory_bruteforcer() - wordlist de diretórios

subdomain_enumerator() - wordlist de subdomínios

Configurar Headers Personalizados
Use a opção 11 (Configurações) para:

Alterar User-Agent

Adicionar cookies de sessão

Contribuições
Contribuições são bem-vindas. Áreas onde pode ajudar:

Adicionar mais payloads de teste

Expandir wordlists

Melhorar deteção de vulnerabilidades

Adicionar novas ferramentas

Corrigir bugs

Melhorar documentação

Licença
Este projeto está licenciado sob a licença MIT - veja o ficheiro LICENSE para detalhes.

Características Técnicas
Multi-threading para maior performance

Código modular fácil de estender

Interface colorida para melhor visualização

Relatórios JSON para integração com outras ferramentas

Tratamento de erros robusto

Configurável para diferentes cenários

Recursos Educacionais
Para aprender mais sobre segurança web:

OWASP Top 10

PortSwigger Web Security Academy

Hack The Box

TryHackMe

Problemas Conhecidos
O SSL Checker pode falhar com certificados auto-assinados

Alguns sites podem bloquear o scanner por excesso de requisições

O Web Crawler pode entrar em loops em sites mal configurados

Suporte
Para questões, sugestões ou relatórios de bugs:

Abra uma issue no GitHub

Envie um pull request com melhorias

Autor
Cybersecurity Student

Projeto educacional para aprendizagem de segurança ofensiva

Uso exclusivamente para estudo e testes autorizados

Lembre-se sempre: Com grandes poderes vêm grandes responsabilidades. Use esta ferramenta com ética e apenas em sistemas que possui ou tem permissão para testar.

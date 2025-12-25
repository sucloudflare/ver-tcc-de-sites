
 <h1>TCP Evidence Scanner & CWE Verification</h1>

<section>
   <h2>Descrição</h2>
   <p>
            Este projeto contém scripts PowerShell para realizar um <strong>scanner TCP</strong> de portas de servidores
            autorizados, coletando evidências reais de serviços abertos e correlacionando com possíveis vulnerabilidades
            (CWEs). O foco é <strong>segurança defensiva</strong>, auditoria de ativos próprios e evidência observável.
   </p>
 </section>
<section>
 <h2>Funcionalidades</h2>
  <ul>
    <li>Verificação de portas TCP abertas (SSH, HTTP, HTTPS, MySQL, PostgreSQL, etc.).</li>
     <li>Coleta de banners de serviços e headers HTTP para evidência.</li>
      <li>Identificação de possíveis vulnerabilidades CWE baseadas em evidência observável.</li>
      <li>Classificação de severidade (Info / Low / Medium).</li>
      <li>Saída estruturada em objetos para fácil análise ou relatório.</li>
   </ul>
 </section>

  <section>
    <h2>Requisitos</h2>
    <ul>
     <li>Windows PowerShell 5.1</li>
     <li>Acesso de rede aos servidores que serão analisados</li>
    <li>Permissão para escanear os IPs/alvos (somente ambientes autorizados!)</li>
 </ul>
 </section>

 <section>
 <h2>Uso</h2>
  <pre><code>
# Importar funções (Test-TcpPort, Get-ServiceEvidence, Invoke-TcpEvidenceScan)
# Executar scanner em um domínio autorizado
$result = Invoke-TcpEvidenceScan "meu-alvo.local"

# Listar resultados completos
$result | Format-List

# Listar apenas serviços verificados
$result | Format-Table IP,Port,Service,Severity,CWE
        </code></pre>
 </section>

 <section>
   <h2>Funções Principais</h2>
   <ul>
   <li><code>Test-TcpPort</code>: Testa se a porta TCP está aberta sem travar.</li>
    <li><code>Get-ServiceEvidence</code>: Coleta banners, headers e outras evidências de serviços.</li>
   <li><code>Invoke-TcpEvidenceScan</code>: Varre IPs e portas, coleta evidências, gera lista de CWEs verificados.</li>
  </ul>
  </section>

   <section>
   <h2>Observações de Segurança</h2>
  <ul>
     <li>Somente utilize em <strong>ambientes autorizados</strong> ou ativos próprios.</li>
     <li>O script não explora vulnerabilidades, apenas verifica evidências observáveis.</li>
     <li>Os CWEs listados são derivados da evidência coletada, não de exploração.</li>
    <li>Evite apontar para servidores de terceiros sem permissão.</li>
     </ul>
   </section>
 <section>
   <h2>Licença</h2>
  <p>
            MIT License – Uso pessoal e acadêmico permitido. Modificações e redistribuição são permitidas com referência ao autor.
    </p>
</section>


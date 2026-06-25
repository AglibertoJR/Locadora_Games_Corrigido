# Testes automatizados adicionados

Os testes foram criados dentro de `src/test/java/com/locadora/demo` e separados por objetivo:

1. `UsuarioServiceTest`
   - `senhaDeveSerCriptografadaNoCadastro`: confirma que a senha cadastrada não é salva em texto plano.
   - `loginNaoAceitaSqlInjectionNaSenha`: confirma que o payload `' OR '1'='1` não autentica o usuário.

2. `JogoServiceTest`
   - `naoExecutaComandoDoSistemaAoSalvarJogo`: valida que o cadastro de jogo não executa comandos do sistema e apenas salva no repositório.

3. `ApiSecurityIntegrationTest`
   - `bloqueiaAcessoSemLogin`: confirma que `/jogos` exige autenticação.
   - `rejeitaXssNoNomeDoJogo`: confirma que payload `<script>` é rejeitado no cadastro de jogo.
   - `validaEmailETelefoneDoCliente`: confirma validação de e-mail e telefone.
   - `naoRetornaStackTraceQuandoJogoNaoExiste`: confirma resposta de erro padronizada sem trace.
   - `usuarioComumNaoPodeDeletarJogo`: confirma controle de acesso por papel para exclusão.

Comandos:

```bash
mvn clean test
mvn clean test jacoco:report
```

Relatório de cobertura:

```text
target/site/jacoco/index.html
```

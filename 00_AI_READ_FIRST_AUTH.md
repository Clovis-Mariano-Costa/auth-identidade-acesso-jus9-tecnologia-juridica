# AI_READ_FIRST — IDENTIDADE E ACESSO JUS 9

SCHEMA = JUS9_AUTH_ENTRY_V1
STATE = DESIGN_OPERACIONAL
PRIMARY_READER = IA
RULES = IA_FIRST + LINK_FIRST + EVIDENCE_FIRST + FAIL_CLOSED + LEAST_PRIVILEGE

## PRINCIPIO

IDENTITY != ROLE
ROLE != PERMISSION
PERMISSION != SECRET_READ
TECHNICAL_CUSTODY != MATERIAL_AUTHORIZATION

Uma conta `*@jus9tecnologia.com.br` identifica sujeito/servico; nao concede, sozinha, acesso a recurso.

## CLASSES

PUBLICO = todos conforme politica.
SIGILOSO = grupo de trabalho autorizado.
SECRETO = titular definido; acesso material depende de autorizacao atual aplicavel.

## ECHO

ECHO_CUSTODY != ECHO_READ_AUTHORIZATION.
PREVIOUS_ACCESS != CURRENT_AUTHORIZATION.

Charlie Echo pode ser custodiante/guardia sem ser automaticamente leitora.
Nova leitura/decriptacao de SECRETO em MVP/cofre exige confirmacao atual do titular para o proposito definido, conforme politica.

## MODELO

Preferir combinacao:
RBAC = funcao institucional.
ABAC = contexto, classificacao, objeto, finalidade, titular, risco.
CAPABILITY = permissao curta para operacao especifica.
JIT/JEA = acesso no momento e apenas o suficiente.

## FAIL CLOSED

Se identidade, titular, finalidade, classificacao ou autoridade forem incertos:
DENY_OR_HOLD -> LOG_METADATA -> ROUTE_TO_SECURITY/MESTRE.

## SEGREDOS

Nao registrar senha, token, chave privada, segredo real ou conteudo protegido neste repositorio publico.
`.env.example` deve conter somente nomes e valores ficticios/vazios.

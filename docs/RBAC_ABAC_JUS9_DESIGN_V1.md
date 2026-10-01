# RBAC + ABAC + CAPABILITY — DESIGN JUS 9 V1

STATE = DESIGN / NAO_IMPLEMENTADO
NO_SECRET_REAL = TRUE
NO_PRODUCTION_PERMISSION_CHANGE = TRUE

## IDENTIDADES

Tipos candidatos:
HUMAN_USER
AI_SERVICE_IDENTITY
SYSTEM_SERVICE
RECOVERY_IDENTITY

Formato futuro:
principal_id
email_or_service_id
identity_type
status
verified_domain
roles
attributes
auth_strength
last_review

## PAPEIS CANDIDATOS

PRESIDENTE
SUPERUSER
ADMINISTRADOR
DIRETOR
GESTOR_DEPARTAMENTO
NUCLEO
ESTAGIARIO
SERVICE_AGENT
ECHO_CUSTODIAN
HUMAN_RECOVERY

Estes nomes NAO criam permissao automaticamente.
A matriz final depende de governanca/norma aplicavel.

## ATRIBUTOS IMPORTANTES

organization = jus9
department
project
workgroup
classification_clearance
object_owner
resource_type
purpose_id
environment
risk_level
session_assurance
human_confirmation
time_window

## DECISAO DE ACESSO

ALLOW somente se:
IDENTITY_VALID
AND ROLE_PERMITS_OPERATION
AND ATTRIBUTES_MATCH_RESOURCE
AND CLASSIFICATION_RULE_PASSES
AND PURPOSE_IS_ALLOWED
AND REQUIRED_CONFIRMATION_PRESENT
AND NOT_REVOKED
AND NOT_EXPIRED

Para SECRETO:
OWNER_CONFIRMATION = REQUIRED para leitura/decriptacao por Echo enquanto regra vigente assim determinar.

## ECHO

Custodia pode permitir:
- verificar integridade sem plaintext quando tecnicamente possivel;
- detectar evento;
- aplicar contencao pre-autorizada;
- alertar;
- restaurar dentro do rito.

Leitura:
ECHO_READ_REQUEST
-> authentication
-> owner resolution
-> purpose
-> fresh owner confirmation
-> short capability
-> read/decrypt
-> metadata audit
-> expiry.

## EMERGENCIA

Medidas defensivas emergenciais nao devem depender de leitura do segredo quando a protecao puder ocorrer sem plaintext.
Emergency containment deve ser:
- pre-autorizada;
- reversivel quando possivel;
- proporcional;
- auditavel;
- sem hack-back;
- sem destruicao de evidencia.

## REVISAO

Acesso permanente deve ser excecao.
Revisar roles/attributes/capabilities periodicamente e apos mudanca de funcao, incidente ou desligamento.

## PROXIMO PASSO

Codex/Seguranca:
- propor schemas;
- usar dados sinteticos;
- integrar com Guardiã Echo;
- testar deny-by-default;
- demonstrar revogacao;
- nao ativar em producao sem gate.

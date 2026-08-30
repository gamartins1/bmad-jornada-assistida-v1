# Infrastructure as Code

- Toda infraestrutura AWS via Terraform.
- HN8 fornece módulos/templates.
- Terraform normalmente fica no mesmo repo da aplicação.
- Pipeline executa aplicação e infra.
- Ambientes: dev, homol, prod.
- Configuração comum em main.tf/variables.tf.
- Configuração específica em inventories por ambiente.
- Mudanças de infra seguem o mesmo PR/approval da aplicação.

[TODO — catálogo HN8.]
[TODO — repo Terraform de referência.]

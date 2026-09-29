# 🤖 Padrões de Engenharia & Cursor Rules

Este repositório contém as regras fundamentais (arquivos `.md`) para o desenvolvimento, arquitetura e revisão de código do nosso projeto. Estas diretrizes foram desenhadas para guiar tanto a equipa de engenharia quanto os nossos assistentes de Inteligência Artificial (como Cursor, Copilot ou Gemini).

## 📌 Diretrizes para a Inteligência Artificial

Se és um assistente de IA a ler este diretório (ex: via `.cursorrules`), deves assumir e aplicar **todas** as regras aqui definidas ao gerar, refatorar ou analisar código. Sob nenhuma circunstância o código gerado deve violar estes princípios.

### Regras de Ouro
1. **Linguagem:** Todo o código-fonte (variáveis, classes, funções, exceções, logs, tabelas) **deve ser escrito estritamente em Inglês**. Documentação e PRs podem ser em Português. Textos visíveis ao utilizador final devem usar sistemas de internacionalização (i18n).
2. **Backend (Laravel & DDD):**
    - Proibido o uso de "God Services". Utilizar `Actions` de verbo e propósito únicos.
    - Respeitar os limites de contexto: Uma `Action` não acede a `Actions` de outros domínios; usar `Orchestrators` para fluxos inter-domínios.
    - Utilizar DTOs para payload, *Skinny Controllers* e devolver respostas através do **Envelope Pattern** (com `data`, `message`, `code`, `status_code`).
    - Evitar `Race Conditions` utilizando `DB::transaction()` encadeado com `lockForUpdate()`.
3. **Frontend (Vue 3 & TS):**
    - Usar obrigatoriamente a **Composition API** (`<script setup lang="ts">`) e tipagem rigorosa.
    - Evitar *HTML inflado* e abusos de `v-if` aninhados; extrair lógica para componentes menores e *composables*.
    - Gerar testes utilizando **Vitest**, focando no comportamento do componente e nas emissões/props.
4. **KISS & Ortogonalidade:** Se houver múltiplas formas de resolver um problema, a IA deve **sempre** escolher a solução mais simples, óbvia e modular, evitando *over-engineering* arquitetural.

### 📚 Navegação Rápida
Consulte o [Manual de Engenharia Limpa (GUIA_ENGENHARIA_LIMPA.md)](./GUIA_ENGENHARIA_LIMPA.md) para explorar em detalhe os 9 pilares da nossa arquitetura.
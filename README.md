# Aviva SEO/GEO — Dashboards públicos

Dashboards do projeto Aviva SEO/GEO (cliente: Aviva | agência: Ivoire).

## Dashboards disponíveis

| Dashboard | URL | Atualização | Propósito |
|---|---|---|---|
| **Semanal SEO/GEO** | [ivoireag.github.io/aviva-seo-geo/](https://ivoireag.github.io/aviva-seo-geo/) | segunda 14h BRT | Snapshot semanal de performance (GSC + GA4 + Ahrefs) |
| **Executivo (sprint)** | [ivoireag.github.io/aviva-seo-geo/executive/](https://ivoireag.github.io/aviva-seo-geo/executive/) | a cada sprint event (kickoff, mid-review, close) | North Star + KRs + tasks + alertas com design system Ivoire |

## Estrutura

```
docs/
├── index.html                # Dashboard semanal
├── _dates.json               # Histórico de datas
├── YYYY-MM-DD/               # Snapshots semanais por data
│   └── dashboard.html
└── executive/                # Dashboard executivo (sprint)
    ├── index.html
    ├── styles.css + ivoire-theme.css
    ├── dashboard.js
    ├── design-tokens.json    # Design system Ivoire extraído do template
    ├── data/snapshot.json    # Dados vivos da sprint
    └── assets/               # Logos Ivoire + Aviva
```

## Dashboard semanal

Gerado automaticamente toda segunda-feira às 14h BRT pelo workflow `/aviva-seo-geo-engine` (script `publish_dashboard_gh_pages.py`). Contém métricas weekly do Google Search Console, GA4 e Ahrefs.

Cada subpasta `docs/YYYY-MM-DD/` contém o snapshot daquela semana. Histórico navegável via dropdown no topo do dashboard.

## Dashboard executivo

Publicado em 2026-04-19 com design system Ivoire extraído do template institucional (`TEMPLATE-Deck-Institucional-Ivoire.pptx`, 47 slides, 13 layouts) via skill `ivoire-document-factory` v2.0.

Consome `design-tokens.json` + `ivoire-theme.css` gerados por `design_system_extractor.py`. `data/snapshot.json` é regenerado automaticamente pelo `aviva-project-orchestrator` (função `build_dashboard_snapshot()` em `generate_control_artifacts.py`) a cada kickoff/midreview/close.

Conteúdo:
- North Star Q2 2026 (% clicks orgânicos absorvidos por aviva.com.br — baseline 7%, meta ≥70% até 2026-06-30).
- Migração de domínios (aviva vs legados + redirects + broken).
- 4 KPIs GSC (Cliques, Impressões, CTR, Posição).
- Progresso por KR (11 KRs dos OKRs Q2 2026 com badges R/Y/G).
- Alertas abertos.
- Tasks comprometidas da sprint ativa.

## Regras duras aplicadas

- Zero ROI / R$ / projeção financeira.
- Nomenclatura oficial Aviva (Rio Quente Resorts plural, Hot Park separado, InCasa/InCanto, Costa do Sauipe).
- Hierarquia de fontes: GSC (1) > GA4 (2) > Ahrefs (3) > crawler (4).
- Tom Ivoire — autoridade técnica/estratégica, sem muletas de IA.

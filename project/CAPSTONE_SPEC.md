# Capstone: Enterprise Knowledge Agent

## Ziel
Ein nachvollziehbarer Assistent, der Fragen über einen begrenzten Bestand technischer oder organisatorischer Dokumente beantwortet, Belege zitiert und bei unzureichender Evidenz keine Antwort erfindet.

## Architektur
1. Ingestion: PDF/Markdown laden und Quellenmetadaten erhalten.
2. Chunking: konfigurierbare Aufteilung.
3. Index: Embeddings und Vector Store hinter einer austauschbaren Schnittstelle.
4. Retrieval: Top-k, Metadatenfilter und optional Reranking.
5. Generation: Modelladapter, strukturierte Antwort, Quellen und Abstention.
6. Tools: ein bis zwei deterministische, erlaubte Tools.
7. Evaluation: feste Fragen, Retrieval-Metriken, Antwortbewertung und Regressionstests.
8. Observability: Request-ID, Latenz, Tokenverbrauch und Fehler; keine Secrets loggen.
9. Interface: zuerst CLI, danach bei Bedarf API/UI.

## Akzeptanzkriterien
- Projekt lässt sich anhand des README starten.
- Ingestion ist reproduzierbar.
- Faktenantworten enthalten Quellen oder das System enthält sich.
- Evaluationsdatensatz ist versioniert.
- Retrieval- und Antwortqualität werden getrennt gemessen.
- Mindestens acht Security-/Adversarial-Tests sind dokumentiert.
- Timeouts, leere Treffer und Providerfehler werden behandelt.
- Secrets liegen in Umgebungsvariablen und nicht in Git.

## Vorschlag für Struktur
```text
enterprise-knowledge-agent/
├── README.md
├── pyproject.toml
├── .env.example
├── src/
│   ├── ingestion/
│   ├── retrieval/
│   ├── generation/
│   ├── tools/
│   ├── evaluation/
│   └── api/
├── tests/
├── evals/
└── docs/
```

## Scope
Erste Version: Single User, read-only. Keine echten Unternehmensdaten ohne Freigabe. Keine Multi-Agent-Komplexität ohne nachgewiesenen Bedarf.

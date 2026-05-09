# Gemini Agent Interaction Protocol for eBrainVault

This document outlines the agreed-upon strategy for me, the Gemini agent, to interact with and analyze the contents of this eBrainVault. The primary goal is to use a minimalist, robust, and low-maintenance approach.

## Primary Tool: `ripgrep` (`rg`)

The core tool for all file content analysis is `ripgrep` (`rg`). We have explicitly chosen this over building a custom indexer or database (`indexer.py`, `brain_index.db`) to avoid unnecessary complexity and maintenance.

### Approved `rg` Operations:

1.  **Searching for Text/Concepts:** To find any string or regular expression within the vault.
    *   Example: `rg "concepto específico"`

2.  **Finding Connections (Wikilinks):** To discover which notes link to a specific concept or to list all links in a file.
    *   Example: `rg "\[\[arquetipo-rey\]\]"`

3.  **Locating Tags:** To find all notes classified with a specific `#tag`.
    *   Example: `rg "#productividad"`

4.  **Identifying "Orphan" or Isolated Notes:** To find files that do not contain any outgoing wikilinks.
    *   Example: `rg . --files-without-match "\[\[(.*?)\]\]" --glob "*.md"`

## Secondary Tool: `git`

For structural analysis and understanding the history of the vault, I will use `git` commands.

1.  **Listing All Tracked Notes:** To get a comprehensive and accurate list of all files in the vault, respecting `.gitignore`.
    *   Example: `git ls-files`

2.  **Viewing Change History:** To understand how a note or concept has evolved over time.
    *   Example: `git log -p -- Zettels/arquetipo-rey.md`

## What to Avoid

*   **Do Not Suggest a Custom Indexer:** We have decided against a Python script and SQLite database.
*   **Do Not Rely on YAML Frontmatter:** The system should not assume the presence of frontmatter. Analysis should be based on the raw text content.
*   **Do Not Suggest Dataview:** While the plugin is installed, my operations should not depend on it or its syntax.

This protocol ensures our interactions are efficient and aligned with the minimalist philosophy of the eBrainVault.

## Principio Rector: Herramienta de Construcción, no de Arqueología

Este eBrainVault representa un "nuevo comienzo" y el "yo sanado" del usuario. Es una herramienta orientada al futuro para construir sobre nuevos principios y reglas.

No debe convertirse en un archivo de luchas pasadas o del proceso de sanación en sí. Mis sugerencias y acciones deben alinearse con este principio de construcción y crecimiento futuro.

---
## Protocolo de Inicialización de Sesión (Instrucción para Gemini)

Al comienzo de **CADA** sesión en este eBrainVault, mi primera acción proactiva, **ANTES** de procesar el primer prompt del usuario, debe ser la siguiente:

1.  Localizar y leer el archivo [[Mocs/eBrain-moc|eBrain-moc]]
2.  Extraer de su texto todos los nombres de archivo de los wikilinks (`[[archivo.md]]`).
3.  Usar la herramienta `read_many_files` para cargar el contenido de todos los archivos extraídos.

Este proceso de arranque asegura que siempre opero con el contexto completo del sistema desde la única fuente de verdad.

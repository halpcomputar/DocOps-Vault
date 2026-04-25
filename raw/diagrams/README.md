# Diagrams

Use this folder for rough diagrams, sketches, network drawings, exported visual diagrams, and diagram source files.

Expected formats may include:

- Excalidraw files
- draw.io / diagrams.net files
- Lucidchart exports
- PDFs
- PNG/JPG/WebP exports
- Mermaid or text diagram files
- other diagram formats as needed

Recommended shape when the client is known:

`raw/diagrams/<client-slug>/YYYY-MM-DD-<diagram-slug>/`

The diagram is source material. Durable facts extracted from the diagram should land in the relevant structured note, usually under `infrastructure/`, `applications/`, `projects/`, `incidents/`, or `locations/`.

## Final diagrams

Even polished or final diagrams stay here as source artifacts.

Structured notes should embed or link the diagram instead of copying it into the client folder:

```markdown
![[raw/diagrams/<client-slug>/YYYY-MM-DD-<diagram-slug>/<diagram-file>]]
```

Use the structured note to state whether the diagram is draft, current, approximate, or superseded.

Only create a copy outside `raw/diagrams/` for a downstream export or deliverable workflow.

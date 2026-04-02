# Daily Reports - Project Guidelines

## Adding a new daily report

When creating a new daily report:

1. **Create the report file** in `YYYY-MM/YYYY-MM-DD.md` with this frontmatter:
   ```yaml
   ---
   layout: report
   title: "Octopus Daily Report — YYYY-MM-DD"
   summary: "One-line summary of key metrics and highlights"
   ---
   ```
   The `layout: report` and `summary` fields are required for the timeline to work.

2. **DO NOT modify `index.md`** — it uses Liquid templating to automatically discover all report pages. Any new report with `layout: report` will appear on the timeline automatically.

3. **DO NOT replace the timeline layout** in `index.md` with a flat list of links. The timeline is the intended design.

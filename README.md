# Clancy Clinical Timeline Prototype

A visual patient timeline demonstrating how clinical information from an Epic / CareConnect record could be organized into encounters, patient messages, symptoms, care transitions, and medication history.

Patient: **Lindsay Clancy**. The demonstration data is manually curated from an existing timeline. It is not an original EHR export, a complete medical chart, or a live connection to Epic or CareConnect. Dates, reports, and medication uncertainty remain explicit; the prototype does not generate new diagnoses or infer medication adherence.

## View

- GitHub Pages: https://alexkdot.github.io/clancy-clinical-timeline/
- Offline: open `standalone-dist/Clancy_Clinical_Timeline.html` in a modern browser.

## Explore

Search the clinical history, filter by entry type, open encounter or medication details, and navigate the chronology. Medication lanes distinguish prescribed / filled, patient-reported use, planned treatment, and inpatient treatment. An interval does not establish continuous daily use.

## Develop

Requires Node.js 22.13 or newer.

```sh
npm ci
npm run dev
npm test
npm run build
```

The build checks TypeScript and creates `docs/index.html` for GitHub Pages and a matching self-contained offline HTML file. Publish the **main** branch's **/docs** folder in the repository's Pages settings. Rebuild and commit both generated files after changing the application or data.

## Data and interface

- `app/clinical-data.ts`: curated demonstration entries and medication intervals.
- `app/page.tsx`: interactive timeline and detail views.
- `app/globals.css`: responsive presentation.
- `tests/clinical-data.test.ts`: content boundaries and data integrity checks.

`recordType` describes the clinical content summarized by an entry. It does not certify access to the original chart or a particular EHR document. The interface uses date-only chronology where exact encounter times are unavailable. Approximate dates and reported history are identified in the entry text.

For a future EHR-generated version, replace the demonstration data with a reviewed import layer that maps authorized clinical records into this schema, retains source record identifiers and actual timestamps, and keeps orders, dispensing, administration, and patient-reported use distinct. No import, upload, authentication, remote storage, or automated clinical extraction is implemented in this prototype.

This repository is independent of the original timeline, with its own deployment and clean history. It does not load the original application's services or data.

# Epiminds Google Ads skills library

Internal, private. Not the public `google-ads-skills` repo next door — never write there.

- Run `/goal` to build or resume the library. It reads `google-ads-skills-index.xlsx`, works the open rows in priority order, and updates the sheet per skill.
- `google-ads-skills-index.xlsx` is the live index. Update its tracking columns with openpyxl; never replace the file or touch the other columns.
- Quality bar: independent practitioners (see `canon.md` once created), not Google best practices. Every claim traces to a dossier.
- Commit after each category: `git add -A && git commit -m "skills: <category>"`.

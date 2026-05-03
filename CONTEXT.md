# Context

## Site purpose

Recruiter/hiring-manager-first personal portfolio. Primary goal: quickly communicate current role, skills, and selected projects to someone scanning for 30 seconds.

## Contact

Email link (`mailto:elizabeth.h.hau@gmail.com`) — no form, no backend. Resume download button hidden until updated PDF is ready — do not link to old PDF.

## Skills (5 categories)

| Category             | Skills                                                                                    |
| -------------------- | ----------------------------------------------------------------------------------------- |
| Languages            | Python, SQL, JavaScript, Java                                                             |
| Cloud & Data         | Azure, Databricks, Spark, Delta Lake, Azure AI Foundry                                    |
| AI / ML              | Scikit-learn, Keras, NLP, LLMs, RAG, Prompt Engineering                                   |
| Data & AI Frameworks | Pandas, PySpark, LangChain, Streamlit                                                     |
| Architecture         | Medallion Architecture, Data Lakehouse, ETL/ELT, Data Modeling, Cloud-native Architecture |

## Tech stack

- **Framework**: Astro (static output, GitHub Pages deploy)
- **Styling**: Custom CSS — dark hybrid aesthetic (see wireframes/dark-hybrid.html)
- **Hosting**: GitHub Pages (same as current)

## Visual design

Dark hybrid aesthetic — Option C. Key traits:

- Dark background (#0d1117) with subtle dot-grid texture
- Neon green accent (#00ff88)
- Monospace font (`SF Mono` / `Fira Code`) for: nav, `//` section labels, category tags, metric blocks, buttons
- Clean sans-serif (`Inter` / system) for: hero name, tagline, all body text, project descriptions, experience content
- Sharp-edged cards (no border-radius), sharp buttons
- Accent metric blocks with left border on project cards

Wireframes saved in `/wireframes/` for reference:

- `dark-technical.html` — Option A (full monospace/terminal)
- `dark-minimal.html` — Option B (clean dark minimal)
- `dark-hybrid.html` — Option C (chosen)

## Projects (5 featured, in display order)

1. **Cycle time data model** (J&J Vision) — integrated 10+ source systems tracking 7B+ lenses/year; 89.6% reduction in 95th-percentile cycle time in one month
2. **Route processing rearchitecture** (Wayfair) — rearchitected delivery route planning; reduced processing time from 30+ min to <1 min, saving 30+ min per warehouse per day
3. **Databricks Lakehouse architecture** (J&J Vision) — designed and stood up Medallion architecture enabling scalable analytics across supply chain functions
4. **GenAI supply chain interface** (J&J Vision) — NL interface via Databricks AI/BI Genie for querying global backorder status and identifying mitigation actions
5. **Warehouse door utilization tool** (Wayfair) — built and launched to 50+ delivery centers; integrated with receiving scanning app and driver app

## Page structure

Single scrollable page with these sections in order:

1. **Hero** — name, tagline, CTA (resume download + contact)
2. **About** — 2-3 sentence bio
3. **Skills/Tech** — scannable list of tools, languages, platforms
4. **Experience** — professional timeline (Wayfair → J&J Vision)
5. **Projects** — 3-5 highlighted projects
6. **Contact** — simple form or email link

No Course Work section (removed — reads as student-era). Multi-page routing dropped in favor of single-page scroll.

## About bio

> I design the systems I build. At J&J Vision I'm both the architect and the engineer — standing up cloud infrastructure, then building the data pipelines and AI tools on top of it. Former SWE at Wayfair. MIT LGO (CS + MBA).

## Owner

Elizabeth Hau — AI Architect & Engineer at J&J Vision. Stood up the team's cloud architecture. Work spans cloud infrastructure, data engineering, analytics, data science, and supply chain AI. MIT LGO (Leaders for Global Operations) — dual M.Eng + MBA, CS & Management.

## Career arc

- **Wayfair** — Software Engineer, Transportation Last Mile · 2016–2020
- **MIT LGO** — M.Eng + MBA (CS & Management) · 2020–2022 — deliberate move to level up technically and strategically before moving into architecture/AI
- **J&J Vision** — AI Architect & Engineer · 2022–present

## Narrative / tagline

> Software engineer. Cloud architect. AI engineer.

Subtext: _the full stack, from infrastructure to intelligence._

The dual architect+engineer role is the key differentiator — she designs the systems she builds.

## Hero label

`// not looking, but listening`

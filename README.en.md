[中文](README.md) | English

# Mankeep Contacts

Manage contacts, relationships, organization history, birthdays, interactions and ledgers inside SiYuan.

**One person, one document. Structured data lives in a native SiYuan database.**

Local-first · native database · three themes · exportable and recoverable · no telemetry

## Why Mankeep

- **Not a contact silo**: every person has both a SiYuan document and a database row. You can use search, backlinks, references and sync as usual.
- **Relationships you can see**: related people, schools, companies, groups and dated experience become a relationship graph with focus, search, privacy mode and PNG export.
- **Data that survives**: interactions, anniversaries, ledgers, organization records and logos are mirrored into a normal SiYuan document named `人脉数据备份` (Contacts Backup). If you keep the person documents, contacts database and backup document, the business data can be restored after reinstalling.

## Features

### Home and contacts

| Capability | Description |
| --- | --- |
| Home dashboard | Contact count, upcoming birthdays, overdue contacts and recent interactions |
| Quick search | Search by name or English name from the home header |
| Cards / table | Two list views with groups, tags, sorting and pagination |
| Group-colored avatars | Avatar colors match the relationship graph groups |
| Two-page detail | Page 1: profile, organization history and anniversaries. Page 2: interactions and ledger |
| One-click actions | Call a phone number, send email, or open a home address in the selected map app |

### Organizations and experience

- Separate records for schools, companies, government bodies and groups, with logo, short name, address and notes.
- Schools support faculties/departments; companies support departments. Departments can be selected directly when adding experience.
- Each experience supports department, role/degree, start/end dates and status.
- Company records support founded date, registered capital, paid-in capital, legal representative and website.
- **Organization details show the office address only**, with a link to the selected map app.

### Calendar, interactions and ledger

- Monthly calendar with Gregorian/lunar birthdays, anniversaries and interactions.
- Click a date to create an interaction and select multiple contacts. A shared event is written to every participant.
- Interaction types: meeting, phone call, voice call, video call, message, gift and other. Meetings support a location.
- Interactions are synced into a "往来记录" section in each person document.
- Anniversaries repeat yearly and appear on the home page.
- Ledger supports money/items/favors, direction, due date, settlement and overdue state.

### Map

![Global map (illustration)](https://gcore.jsdelivr.net/gh/ccztao/siyuan-mankeep@main/screenshots/global-map.jpg)

- Aggregates home addresses and current company addresses, grouping contacts by address.
- Home and company addresses support precise point selection and store six-decimal GCJ-02 coordinates.
- Reuse an existing home address and share its coordinates; a family only needs to locate once.
- The global map shows all saved coordinates: red for home, blue for company. Click a marker to see the address and contacts.
- Choose **Amap (default) or Baidu Maps** in Settings for opening addresses.
- An Amap Web Service Key enables door-level search by community, road or POI.

### Relationship graph

![Relationship graph (illustration)](https://gcore.jsdelivr.net/gh/ccztao/siyuan-mankeep@main/screenshots/graph.jpg)

- Bidirectional relationships and organization history arranged as a compact force-directed graph.
- Node size by connection count and color by group; focus on me, focus on an organization, and search highlighting.
- Zoom, drag, fit to view and re-layout.
- **Privacy mode keeps surnames and hides given names**; organization names stay visible.
- **PNG export**: keeps the current theme, edges, nodes and organization logos; no dot grid; 6× resolution.

### Data and recovery

- vCard 3.0 import/export, with common 2.1/4.0 forms, folded lines, GBK and quoted-printable support.
- JSON export containing interactions, anniversaries, ledgers, organization records and experience.
- Interactions, anniversaries, ledgers, organization records and logos are mirrored into `人脉数据备份`.
- If the plugin and its private data are removed, keeping the person documents, contacts database and backup document is enough to restore business data.
- Restore from backup, or sync existing interactions into person documents with one click.

### Themes

![Three themes](https://gcore.jsdelivr.net/gh/ccztao/siyuan-mankeep@main/screenshots/theme-showcase.jpg)

LinkedIn Blue, Warm Orange and Pine Green. Switch in Settings → Theme Colors. Light and dark modes are both supported.

## UI

Liquid Glass surfaces, blurred panels, inner highlights, soft shadows and pill controls. Open Mankeep from the top bar on desktop; mobile has a full-screen entry.

## Installation

1. `pnpm install && pnpm build`
2. Copy the contents of `dist/` to `data/plugins/siyuan-mankeep/` in your workspace
3. Restart SiYuan and enable **Mankeep Contacts** in Settings → Marketplace → Installed
4. Click the Mankeep icon in the top bar and follow the wizard

## Development

```bash
pnpm install
pnpm dev       # watch build to dev/
pnpm build     # production build to dist/
pnpm check     # TypeScript type check
pnpm package   # create package.zip
```

## Data and recovery

| Data | Location |
| --- | --- |
| Person documents, contacts database | Native SiYuan documents / database |
| Interactions, anniversaries, ledger, organization records, home coordinates | Plugin JSON, mirrored to `人脉数据备份` |
| Settings, theme, workspace anchors, Amap key | Plugin JSON |
| Backup document | Normal SiYuan document `人脉数据备份` |

To restore:

1. Reinstall the plugin.
2. Use the original notebook name during initialization; the existing contacts database is reused.
3. Go to Settings → Data Export → Restore from backup document.

Theme preferences are not included in the backup. If the backup document is also deleted, private plugin data cannot be recovered.

## Known limitations

- No AI recognition, meeting-note capture, or CardDAV/CalDAV sync.
- A contact can have multiple organization experiences. The database organization column shows the current primary organization; full history lives in plugin data.
- The graph only shows related people and organization history; it does not infer relationships.
- Map search depends on OpenStreetMap/Photon or an Amap Web Service Key. Without a key, coverage of Chinese communities and POIs is limited.

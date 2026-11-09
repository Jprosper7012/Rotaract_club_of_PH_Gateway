# Club content

The website uses eight distinct entries transcribed from the supplied club materials. Duplicate flyers and repeated photograph references are not imported as additional events. The importer removes only the original demo records by exact title/email; it does not truncate tables or remove contact messages.

Reimport (idempotent): `npx tsx src/db/import-club-events.ts`

## Source handling

- Memorial Fellowship: honouring Late Rtr Ubochi Chinweoke Gloria (1997–2023). Saturday, 14 November 2026; 4 PM for 4:30 PM; City Express Hotel, Mile 4, Port Harcourt, Rivers State. Theme: A Legacy of Service, Wisdom and Friendship. No additional biography is invented.
- ENISC Bee 2.0: Equip the Nigerian School Child. Organiser: Rotaract Club of Port Harcourt Cosmopolitan Hybride. PH Gateway appears among the sponsors/partners, not as the lead organiser. Open to students in JSS1–JSS3. Advertised prizes: ₦100,000 / ₦70,000 / ₦50,000. Venue: Gateway International Church, 98 Illoabuchi, Mile 2 Diobu, Port Harcourt. New date: 7 November; 9 AM prompt. **The flyer gives no year.** `eventDate` remains null; `sourceDateLabel` preserves the partial date; confirmation is required and calendar/registration are blocked. It is not classified as a campaign. Published enquiries: 08136567556, 08029226150, eniscbee@gmail.com, @eniscbee. The photographs do not prove a year or an attendance total.
- Inaugural Fellowship: 25 July 2026; 4 PM for 4:30 PM; City Express Hotel, Mile 4, Port Harcourt.
- Splash Out Polio: 17 October 2026; 1 PM; Lemaco Event Centre, Ada-George Road, Port Harcourt. Rivers New City is the presenting club; PH Gateway is a partner.
- Read to Rise: 14 October 2026; 10 AM; Holy Rosary College, Old GRA. Organiser credits follow Rotaract Club of Port Harcourt and Interact Club of Holy Rosary College. The figure 30 is a target, not a verified outcome.
- Handing Over Ceremony: the numeric date 27 June 2026 is retained. The flyer says Friday, but that date is a Saturday. Marked for confirmation; no calendar download or RSVP.
- Health Talk: 21 June 2025; 4 PM; Google Meet. The original year is preserved. No joining link is invented.
- End Polio Now: undated awareness material credited to the clubs shown. No vaccination event/date/venue is invented.

All complete event instants use WAT (UTC+1). Status labels follow the current Lagos calendar date. Upcoming featured events take priority on the homepage; a partial date is never assigned an assumed year for sorting or registration.

## Original media

The images were visible in the conversation, but their binary files were not mounted or exposed as downloadable URLs in the workspace. The eight SVG covers are labelled as adapted web artwork, not original flyers or photographs. The memorial cover does not invent or replace the honouree’s portrait. No stock photographs are presented as club activities.

Original JPG flyers are supported at `public/uploads/<event-slug>.jpg`, including:

- `public/uploads/memorial-fellowship.jpg`
- `public/uploads/enisc-bee-2.jpg`
- `public/uploads/inaugural-fellowship.jpg`
- `public/uploads/splash-out-polio.jpg`
- `public/uploads/read-to-rise.jpg`
- `public/uploads/handing-over-ceremony.jpg`
- `public/uploads/health-talk-your-health-your-wealth.jpg`
- `public/uploads/end-polio-now.jpg`

Original photographs are imported only when their files exist:

- `public/uploads/read-to-rise-group.jpg`
- `public/uploads/read-to-rise-books.jpg`
- `public/uploads/read-to-rise-presentation.jpg`
- `public/uploads/enisc-bee-2-participants.jpg`
- `public/uploads/enisc-bee-2-competition-hall.jpg`

The importer associates each photograph with its event, updates existing captions without creating duplicates, and skips missing files instead of publishing broken images. Captions describe visible activities without identifying students or inferring a year.

## Validation

- `npx tsx scripts/smoke-test.ts` checks all eight entries, tribute details, WAT calendars, partial-date safeguards, public pages/gallery, contact persistence, and registration deduplication.
- `scripts/browser-check.mjs` uses an installed or isolated Playwright module (`PLAYWRIGHT_MODULE`), with optional `CAPTURE_SCREENSHOTS=1`.

Contact messages and expressions of interest are stored in PostgreSQL through Drizzle. No email delivery service is configured or claimed. Public member APIs omit private contact fields.

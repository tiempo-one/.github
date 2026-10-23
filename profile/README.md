# Tiempo

**Scheduling infrastructure for booking platforms.** One API for availability, holds and bookings
across every business you host. Exactly one customer wins each slot, and every change reaches you
as a signed webhook.

Your platform keeps its services, prices, customers and payments. Tiempo keeps the time: staff,
rooms and courts with working hours, availability search, holds that expire while a customer
pays, classes with seats, recurring bookings that keep their local time through clock changes,
and test and live modes.

```bash
npm install @tiempo/sdk
```

```ts
import { Tiempo } from '@tiempo/sdk'

const tiempo = new Tiempo(process.env.TIEMPO_API_KEY!) // a test key, tpt_…
const shop = tiempo.withAccount('acct_…')

const { slots } = await shop.availability.search({
  from: '2027-01-04T00:00:00Z',
  to: '2027-01-05T00:00:00Z',
  segments: [{ resources: ['res_ann…'], duration_minutes: 45 }],
})
const hold = await shop.bookings.create({ segments: slots[0].segments })
await shop.bookings.confirm(hold.id)
```

## Repositories

| Repository | What it is |
| --- | --- |
| [tiempo-node](https://github.com/tiempo-one/tiempo-node) | The TypeScript SDK, published on npm as [@tiempo/sdk](https://www.npmjs.com/package/@tiempo/sdk) |
| [booking-starter](https://github.com/tiempo-one/booking-starter) | A barbershop booking app on Next.js: availability, holds, Stripe or test payments, and a double-booking race test. Fork it |

## Start here

- [Quickstart](https://tiempo.one/docs/quickstart): your first booking in ten minutes, with curl
- [Booking starter](https://github.com/tiempo-one/booking-starter): a whole app, running locally in five minutes
- [Build with AI](https://tiempo.one/docs/build-with-ai): a rules file for Claude Code, Cursor and Lovable
- [Why AI-built booking apps double-book](https://tiempo.one/docs/double-booking)
- [API reference](https://tiempo.one/docs) and the [OpenAPI description](https://api.tiempo.one/openapi.json)
- [Pricing](https://tiempo.one/pricing): free test mode, then 1p a booking or a subscription from £9 a month

Tiempo is run by Double-Tap Development Ltd, registered in Scotland. Questions:
info@doubletapdevelopment.com.

# Indoware store

A single-page menswear store for blazers, Indo-western and Jodhpuri jackets with an animated hanging rack, a 3D product view,
product pages, a cart, checkout and an order confirmation page.

## How to open it

Double-click `index.html`. It opens in any modern browser (Chrome, Edge,
Firefox, Safari). No installation or server is needed.

Fonts load from Google Fonts, so connect to the internet for the intended
look. Without a connection, the page falls back to system fonts.

## Trying the checkout

- Discount codes: `INDOWARE10` (10% off) and `WELCOME5` ($5 off).
- Card that succeeds: `4242 4242 4242 4242`, any future expiry, any 3-digit code.
- Card that is declined: `4000 0000 0000 0002`.
- No money is taken. The cart and orders are saved only in your browser.

## Changing the products

Open `index.html` in a text editor and find `const P = [` near the top of
the `<script>` section. Each line is one product:

- `name`, `cat` (category), `price`, `desc` (description)
- `cat` must be one of the names in `CATS`: `Casual blazers`, `Formal blazers`,
  `Indo western` or `Jodhpuri`. These are the filter buttons above the rail.
- `type`: `casual`, `formal`, `indo` or `jodh`
- `c`: main colour as a hex code (used for the narrow side view on the rail),
  `cn`: colour name
- `out`: sizes that are sold out, for example `['XS','S']`

Each product needs two photos in the `images` folder, named after its `id`:
`images/<id>.webp` (front) and `images/<id>-back.webp` (back). Use a
transparent background, a 4:5 shape (the current ones are 640 × 800) and show
the piece on a hanger with the hook near the top, so it lines up on the rail.

## Going live

To accept real orders you need:

1. A payment provider such as Stripe or Razorpay, whose card fields replace
   the demo card inputs.
2. A backend with a database that stores products, stock and orders, and
   that recalculates prices itself.
3. An email service for order confirmations.

The demo payment happens in the checkout form's `submit` handler (search for
`coForm`). That is where you would call your server instead.

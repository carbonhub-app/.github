<div align="center">
  <table border="1">
    <tr>
      <td align="center" style="padding: 20px;">
        <h3>📢 Domain & Email Migration Notice</h3>
        <p>Since <b>19 March 2026</b>, Carbonhub has transitioned to new domains as <code>carbonhub.app</code> was not renewed:</p>
        <p>🌐 <b>Website:</b> <a href="https://carbonhub.faizath.com">carbonhub.faizath.com</a> (formerly <i>carbonhub.app</i>)<br>
        ⚙️ <b>API:</b> <a href="https://carbonhub-api.faizath.com">carbonhub-api.faizath.com</a> (formerly <i>api.carbonhub.app</i>)<br>
        📧 <b>Email:</b> <a href="mailto:contact@carbonhub.faizath.com">contact@carbonhub.faizath.com</a> (formerly <i>contact@carbonhub.app</i>)<br>
        🛰️ <b>CDN:</b> <a>carbonhub-cdn.faizath.com</a> (formerly <i>cdn.carbonhub.app</i>)<br>
        📈 <b>Status Pages:</b> <a href="https://status.faizath.com/status/carbonhub">https://status.faizath.com/status/carbonhub</a> (formerly <i>status.carbonhub.app</i>)
        </p>
      </td>
    </tr>
  </table>
</div>

<div align="center">

<img src="profile/assets/logo.png" alt="CarbonHub logo" width="100%">

# CarbonHub

**Make Every Emission Count**

Track emissions, earn blockchain-powered rewards, and trade carbon credits — all in real time,
all in one intelligent platform.

[**Live app**](https://carbonhub.faizath.com) · [**API & docs**](https://carbonhub-api.faizath.com)

<br>

![Next.js](https://img.shields.io/badge/Next.js-16-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-5.9-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-4-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)

![Bun](https://img.shields.io/badge/Bun-1-000000?style=for-the-badge&logo=bun&logoColor=white)
![Elysia](https://img.shields.io/badge/Elysia-1.4-1A1A2E?style=for-the-badge)
![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose%208-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![Solana](https://img.shields.io/badge/Solana-SPL%20Token-14F195?style=for-the-badge&logo=solana&logoColor=black)

![Docker](https://img.shields.io/badge/Docker-CapRover-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Cloudflare Pages](https://img.shields.io/badge/Cloudflare%20Pages-Static%20export-F38020?style=for-the-badge&logo=cloudflarepages&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.7-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![ESP32](https://img.shields.io/badge/ESP32-MQ135-E7352C?style=for-the-badge&logo=espressif&logoColor=white)

![II3240-24](https://img.shields.io/badge/II3240--24-STEI%20ITB-1B3A6B?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-3DA639?style=for-the-badge)

<br>

<img src="profile/assets/carbonhub.webp" alt="CarbonHub overview" width="100%">

</div>

---

## What is CarbonHub?

**CarbonHub** turns a carbon allowance into something you can actually hold and trade. You connect
a Solana wallet, sign a one-time challenge to prove you own it — there is no password anywhere —
and land on a dashboard showing your carbon credit balance beside the emission quota you have left
for the year. From there you either **withdraw quota** into spendable credits, or take them to the
trading desk and swap between **ECFCH** (the carbon credit token) and **EURCH** (its euro-denominated
counterpart) at a rate tracking the live carbon futures price. Every order is a real SPL token
transfer you approve in your own wallet, and it settles **signed → transferred → minted** before the
confirmation returns.

Companies register the same way and receive an API key scoped to them alone. That key is what an
ESP32 sensor node in the field uses to push CO₂ readings to the platform: the device filters its own
MQ135 readings, scores them against a locally trained model, and reports normal samples and
anomalies to separate endpoints. Emissions therefore arrive from hardware rather than from a form,
and the quota shown on the dashboard is drawn down by what was actually measured.

### Built for

CarbonHub was built by a five-person team for **Information Systems and Technology Engineering
(II3240-24)** at **STEI ITB**, as a working answer to how a carbon market stays auditable when the
usual answer is a spreadsheet. It is deployed and running: the web app on Cloudflare Pages, the API
on CapRover, and the token contracts on Solana.

### Highlights

- **Passwordless by design** — authentication is a `tweetnacl` signature check against a Solana
  public key, so the platform never stores a credential that could leak. Device ingest uses a
  separate per-company `x-api-key`, which cannot be swapped for a user session.
- **Swaps are settled from the signed transfer, not the request** — `/swap/execute` decodes the
  transaction it was handed, finds the SPL transfer instruction, and mints against the amount and
  destination actually signed. Naming a different token or a larger figure in the request body
  changes nothing.
- **Replay-safe payouts** — a unique index on the transaction signature claims each swap before any
  token is minted, so two requests carrying the same signed transaction settle exactly once.
- **Confirmation that survives the round trip** — a wallet-signed transaction loses its blockhash
  lifetime in the wire format, so execution confirms by polling the signature itself rather than
  dereferencing a lifetime that decoding cannot restore.
- **Anomaly detection at the edge** — the ESP32 node runs a moving-average filter and z-score
  scoring against a scikit-learn model on-device, so a faulty reading is flagged where it is taken
  instead of after it has entered the ledger.
- **Prices from a live market** — the exchange rate is read from a real carbon futures quote and
  cached, with the trading desk charting the same instrument through TradingView.

---

## Screenshots

<table>
<tr>
<td width="50%" align="center"><b>Choosing a wallet</b><br><br><img src="profile/assets/screenshots/1.png" alt="Wallet chooser offering Brave Wallet and Phantom" width="100%"></td>
<td width="50%" align="center"><b>Phantom — connection request</b><br><br><img src="profile/assets/screenshots/2.png" alt="Phantom wallet asking to connect to carbonhub.faizath.com" width="100%"></td>
</tr>
<tr>
<td width="50%" align="center"><b>User or company login</b><br><br><img src="profile/assets/screenshots/3.png" alt="Login menu offering User Login and Company Login" width="100%"></td>
<td width="50%" align="center"><b>Phantom — signing the auth challenge</b><br><br><img src="profile/assets/screenshots/4.png" alt="Phantom wallet signing a hex challenge message on Solana" width="100%"></td>
</tr>
<tr>
<td width="50%" align="center"><b>Dashboard — credits and quota</b><br><br><img src="profile/assets/screenshots/5.png" alt="Dashboard showing carbon credit balance, wallet status and annual emission quota" width="100%"></td>
<td width="50%" align="center"><b>Withdrawing emission quota</b><br><br><img src="profile/assets/screenshots/6.png" alt="Withdraw emission quota dialog with an amount slider" width="100%"></td>
</tr>
<tr>
<td width="50%" align="center"><b>Trading desk — placing an order</b><br><br><img src="profile/assets/screenshots/7.png" alt="Trading page with a carbon futures candlestick chart and an order panel" width="100%"></td>
<td width="50%" align="center"><b>Phantom — confirming the swap</b><br><br><img src="profile/assets/screenshots/8.png" alt="Phantom wallet confirming a one ECFCH transfer and its network fee" width="100%"></td>
</tr>
<tr>
<td width="50%" align="center"><b>Order filled, signature returned</b><br><br><img src="profile/assets/screenshots/9.png" alt="Success notification showing the Solana transaction signature for a filled sell order" width="100%"></td>
<td width="50%" align="center"><b>Minted balances in the wallet</b><br><br><img src="profile/assets/screenshots/10.png" alt="Phantom wallet listing SOL, ECFCH and EURCH token balances" width="100%"></td>
</tr>
</table>

---

## The team behind CarbonHub

<div align="center">
<table>
<tr>
<td align="center" width="20%">
<a href="https://github.com/jijiau"><img src="https://github.com/jijiau.png" width="100" height="100" alt="Jihan Aurelia"></a><br>
<b>Jihan Aurelia</b><br>
<sub><i>Frontend Developer</i></sub><br><br>
<a href="https://github.com/jijiau">GitHub</a> · <a href="https://www.linkedin.com/in/jihanaurelia/">LinkedIn</a>
</td>
<td align="center" width="20%">
<a href="https://github.com/Serenadacinta"><img src="https://github.com/Serenadacinta.png" width="100" height="100" alt="Serenada Cinta"></a><br>
<b>Serenada Cinta</b><br>
<sub><i>UI/UX Designer</i></sub><br><br>
<a href="https://github.com/Serenadacinta">GitHub</a> · <a href="https://www.linkedin.com/in/serenada-cinta-sunindyo-77aa55283/">LinkedIn</a>
</td>
<td align="center" width="20%">
<a href="https://github.com/aththariq"><img src="https://github.com/aththariq.png" width="100" height="100" alt="Aththariq Lisan"></a><br>
<b>Aththariq Lisan</b><br>
<sub><i>Frontend Developer</i></sub><br><br>
<a href="https://github.com/aththariq">GitHub</a> · <a href="https://www.linkedin.com/in/aththariqlisan/">LinkedIn</a>
</td>
<td align="center" width="20%">
<a href="https://github.com/nasywaanaa"><img src="https://github.com/nasywaanaa.png" width="100" height="100" alt="Nasywaa Anggun"></a><br>
<b>Nasywaa Anggun</b><br>
<sub><i>Backend Developer</i></sub><br><br>
<a href="https://github.com/nasywaanaa">GitHub</a> · <a href="https://www.linkedin.com/in/nasywaa-anggun-athiefah/">LinkedIn</a>
</td>
<td align="center" width="20%">
<a href="https://github.com/faizath"><img src="https://github.com/faizath.png" width="100" height="100" alt="Faiz Atharrahman"></a><br>
<b>Faiz Atharrahman</b><br>
<sub><i>Backend Developer</i></sub><br><br>
<a href="https://github.com/faizath">GitHub</a> · <a href="https://www.linkedin.com/in/faizath/">LinkedIn</a>
</td>
</tr>
</table>
</div>

---

## Repositories

| Repository | Description | Tech stack | Live |
|---|---|---|---|
| [**carbonhub-web**](https://github.com/carbonhub-app/carbonhub-web) | Next.js 16 statically exported single-page app — the landing site, wallet login, dashboard and trading desk. | Next.js · React 19 · TypeScript · Tailwind CSS · Lightweight Charts | [carbonhub.faizath.com](https://carbonhub.faizath.com) |
| [**carbonhub-api**](https://github.com/carbonhub-app/carbonhub-api) | Bun + Elysia REST API — wallet-signature auth, emission collection and ECFCH/EURCH token swaps on Solana. | Bun · Elysia · MongoDB · Solana Kit · SPL Token | [carbonhub-api.faizath.com](https://carbonhub-api.faizath.com) |
| [**carbonhub-aiot**](https://github.com/carbonhub-app/carbonhub-aiot) | ESP32 firmware and a Python companion — samples CO₂ on an MQ135, scores anomalies locally and reports both to the API. | ESP32 · MQ135 · Python · scikit-learn · NumPy | — |
| [**carbonhub-mobile**](https://github.com/carbonhub-app/carbonhub-mobile) | Expo / React Native client — a cross-platform interface for tracking a carbon footprint on the move. | Expo · React Native · Gluestack UI · NativeWind · Expo Router | — |
| [**.github**](https://github.com/carbonhub-app/.github) | This organization profile and its assets. | Markdown | — |

> [!NOTE]
> The deployed platform runs against the Solana **devnet**. ECFCH and EURCH are test-network SPL
> tokens, so balances and swaps carry no real-world value.

---

<div align="center">
<sub>Built at <b>STEI ITB</b> for <b>Information Systems and Technology Engineering (II3240-24)</b>.</sub>
</div>

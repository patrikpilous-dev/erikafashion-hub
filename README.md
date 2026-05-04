# Erika Fashion · Dashboard hub

Centrální vstupní bod pro marketingové dashboardy. Po přihlášení nabídne výběr ze
dvou oddělených dashboardů.

**Live:** https://patrikpilous-dev.github.io/erikafashion-hub/

## Co je v hubu

- 📦 [Dashboard objednávek](https://patrikpilous-dev.github.io/erikafashion-dashboard/) — klouzavý rok prodejů s napojením na počasí
- 🔍 [Share of Search](https://patrikpilous-dev.github.io/erikafashion-sos/) — kompetitivní analýza brandového vyhledávání

## Přihlášení

Heslo je hashované přes SHA-256 (klientská gate, ne plnohodnotná autentizace —
data v cílových dashboardech jsou ostatně anonymizovaná).

Aktuální heslo: nastavené v `index.html` (řádek `PWD_HASH`).

### Změna hesla

V prohlížeči konzole:

```js
crypto.subtle.digest('SHA-256', new TextEncoder().encode('NOVE_HESLO'))
  .then(b => console.log(Array.from(new Uint8Array(b)).map(x=>x.toString(16).padStart(2,'0')).join('')));
```

Vlož vypsaný hex string do `index.html` jako `PWD_HASH` a pushni.

## Bezpečnost

Tohle je `client-side gate` — kdokoli, kdo zná přímou URL cílového dashboardu,
ho může otevřít bez hesla. Hub jen schovává URL a komfortní přechod.

Pro plnou autentizaci by bylo potřeba:
- Privátní GitHub repo + GitHub Enterprise Pages (placené), nebo
- Cloudflare Access nad doménou, nebo
- Hostovat dashboardy na Vercel/Netlify s heslovou ochranou.

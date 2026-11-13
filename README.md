# modelesieci.pl

Strona główna — Mikołaj Jaczyński · Sieci wod-kan w praktyce.
Publikowana przez GitHub Pages (gałąź main, katalog główny), domena w `CNAME`.

Domena główna od 13.11.2026 (wcześniej była nią `jaczynski.com.pl`, zob. historia gita
repozytorium `mikolajjaczynski-dev/jaczynski.com.pl`).

## Układ strony

- **Komputer:** u góry poziome logo (sygnet + nazwisko i usługi), pod nim animacja.
- **Telefon (szerokość ≤ 600 px):** pierwszy ekran zajmuje całą wysokość: pionowe
  logo (duży sygnet, pod nim nazwisko, „SIECI WOD-KAN W PRAKTYCE”, usługi w dwóch
  liniach) i strzałka w dół. Dalej animacja przewijana krokami.
- Ikona LinkedIn w prawym górnym rogu logo: 32 px na komputerze, 72 px na telefonie.

## Google

- `robots.txt`: pozwala indeksować całą stronę i wskazuje mapę strony.
- `sitemap.xml`: lista adresów. Dodając podstronę, dopisz ją tutaj i zmień `lastmod`.
- `index.html`: `<link rel="canonical" href="https://modelesieci.pl/">`.
- Google Search Console: usługa typu Domena `modelesieci.pl`, weryfikacja
  rekordem TXT `google-site-verification=…` w VH.pl (na domenie głównej),
  mapa strony `https://modelesieci.pl/sitemap.xml` zgłoszona w zakładce „Mapy witryn”.

## Domeny dodatkowe — przekierowania

`modelesieci.pl` jest jedyną domeną z treścią (domena kanoniczna dla Google).
Pozostałe domeny przekierowują tutaj. Identyczna treść pod trzema domenami
byłaby dla Google duplikatem.

| Domena | Repozytorium | Przekierowanie |
| --- | --- | --- |
| `jaczynski.com.pl` | `mikolajjaczynski-dev/jaczynski.com.pl` | → `https://modelesieci.pl/` |
| `praktykasieci.pl` | `mikolajjaczynski-dev/praktykasieci.pl` | → `https://modelesieci.pl/` |

**Dlaczego tak:** VH.pl bez hostingu nie ma opcji przekierowania domeny, a
GitHub Pages nie wysyła nagłówka HTTP 301. Dlatego oba repozytoria zostały na
GitHub Pages (DNS: A×4 na GitHub, `www` CNAME, TXT weryfikacji), ale
ich `index.html` i `404.html` to strony-przekierowania:

- `<meta http-equiv="refresh" content="0; url=https://modelesieci.pl/">`:
  natychmiastowe odświeżenie, które Google traktuje jak przekierowanie stałe,
- `<link rel="canonical" href="https://modelesieci.pl/">`,
- `location.replace(…)` w JavaScripcie.

Dzięki `404.html` każda podstrona domeny dodatkowej też przekierowuje.
HTTPS działa, bo certyfikat wystawia GitHub Pages.

**Nie usuwaj tych repozytoriów.** Bez nich domeny pokażą błąd 404 z GitHuba.
Każde repozytorium ma w `CNAME` swoją domenę — przy zmianie domeny głównej
zamienia się tylko zawartość plików, ustawienia GitHub Pages zostają bez zmian.

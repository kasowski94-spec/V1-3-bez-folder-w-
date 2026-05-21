# ElewacjaPro — wersja BEZ FOLDERÓW

## Co się zmieniło

Ikony i screenshots są **wbudowane bezpośrednio w `manifest.json`** jako Data URI (base64).
Nie musisz wgrywać żadnych folderów `icons/` ani `screenshots/` na GitHub.

## Pliki do wgrania (wszystkie w głównym katalogu)

| Plik | Rozmiar |
|---|---|
| `index.html` | 230 KB |
| `sw.js` | 2 KB |
| `manifest.json` | 215 KB *(zawiera wbudowane ikony i screenshots)* |
| `pdf-font.js` | 75 KB |

**TO WSZYSTKO.** Cztery pliki, jeden katalog. Bez folderów.

## Wgranie na GitHub Pages (3 minuty)

1. Wejdź na github.com → swoje repo
2. Otwórz katalog główny repo
3. Kliknij **Add file → Upload files**
4. **Przeciągnij wszystkie 4 pliki** (`index.html`, `sw.js`, `manifest.json`, `pdf-font.js`) — nie foldery, tylko pliki
5. Na dole: **Commit changes**
6. Settings → Pages → branch: main / root → Save
7. Po 1-2 minutach masz URL — otwórz go

## Test po wgraniu

W przeglądarce wejdź na:

- `https://twoj-url/manifest.json` → powinien pokazać tekst JSON ze zaszyfrowanymi obrazkami (długi)
- `https://twoj-url/index.html` → powinna otworzyć się aplikacja
- `https://twoj-url/sw.js` → powinien pokazać kod service workera

Jeśli któryś daje 404 — plik nie został wgrany do dobrego miejsca.

## PWABuilder

1. Wejdź na pwabuilder.com
2. Wklej URL aplikacji (np. `https://login.github.io/elewacjapro/`)
3. **Start**
4. Sprawdź raport:
   - Manifest powinien być teraz pełen (45/45 lub blisko)
   - Service Worker — zielony
   - App Capabilities — zielony

5. Package For Stores → Android → Generate Package
6. Pobierz APK i wyślij na telefon

## Co jeśli PWABuilder dalej narzeka

Tym razem nie powinien — bo nie ma odwołań do plików, tylko data URI. Ale gdyby coś:

**Problem: "Specify your native app ID"**
- To nie jest błąd manifest. To pole do uzupełnienia w samym PWABuilder podczas pakowania (Etap 3).
- Wpisz `com.twojanazwa.elewacjapro` (zamień `twojanazwa` na coś unikalnego)

**Problem: manifest się ładuje wolno**
- Bo jest 215 KB. To duży manifest, ale PWA-Builder to akceptuje (limit to 1 MB).
- W produkcji może być wolniejszy load — to normalne dla samowystarczalnych PWA.

## Jeśli chcesz przywrócić foldery (zaawansowane)

Możesz wrócić do struktury z folderami `icons/` i `screenshots/` używając poprzedniej wersji
paczki ElewacjaPro.zip — wtedy manifest.json będzie mniejszy ale potrzebujesz wgrać folderу.

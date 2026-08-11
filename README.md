# 🧪 E2E Automation Tests - System Reklamowy & Słowniki

Projekt zawiera zestaw testów E2E (End-to-End) dla panelu administracyjnego z wykorzystaniem frameworka **Playwright** oraz **TypeScript**. 

## 🛠️ Technologie
*   **Framework:** Playwright Test
*   **Język:** TypeScript
*   **Zarządzanie środowiskiem:** `dotenv` (plik `.env` do przechowywania np. loginów, haseł i URL)

## 📂 Struktura testów
Projekt został podzielony na logiczne moduły biznesowe, co ułatwia zarządzanie kodem i niezależne uruchamianie poszczególnych pakietów:

*   `01_autentykacja_i_profil.test.ts` - Logowanie, obsługa sesji i zarządzanie kontem.
*   `02_zarzadzanie_reklamami.test.ts` - Cykl życia reklamy (CRUD), wyszukiwanie, zamykanie modali.
*   `03_nawigacja_po_stronie.test.ts` - Smoke testy dla głównego menu i przejść między ekranami.
*   `04_tabele_urzadzenia.test.ts` - Weryfikacja danych w tabelach oraz sortowanie.
*   `05_slowniki_lokalizacje.test.ts` - Zarządzanie słownikiem lokalizacji (aktywacja/dezaktywacja).
*   `06_slowniki_gabinety.test.ts` - Zarządzanie słownikiem gabinetów (aktywacja/dezaktywacja).
*   `07_slowniki_tagi.test.ts` - Zarządzanie słownikiem tagów (aktywacja/dezaktywacja).

## 🚀 Uruchamianie testów (Ściągawka CLI)

Poniżej znajdują się najważniejsze polecenia do uruchamiania testów w terminalu:

| Cel | Polecenie |
| :--- | :--- |
| **Uruchomienie wszystkich testów (headless)** | `npx playwright test` |
| **Uruchomienie konkretnego pliku** | `npx playwright test 02_zarzadzanie_reklamami.test.ts` |
| **Tryb graficzny (UI)** | `npx playwright test --ui` |
| **Tylko w przeglądarce Chromium** | `npx playwright test --project=chromium` |

### 🛡️ Weryfikacja stabilności (Flaky Tests)
Aby upewnić się, że testy są w 100% stabilne (np. po refaktoringu) i odporne na asynchroniczność aplikacji (React re-renders), używamy flagi wymuszającej iteracje:
```bash
# Uruchamia konkretny plik 5 razy z rzędu
npx playwright test 02_zarzadzanie_reklamami.test.ts --repeat-each=5

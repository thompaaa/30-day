# ⚽ Fotbollsträning – planerare

En enkel webbapp för att planera träningspass för ett fotbollslag (7–8 år).
Allt ligger i `index.html` – ingen server, ingen databas, inga beroenden.

## Funktioner

- **Övningsbank** med alla övningar, filtrerbar per kategori och sökbar.
- **Veckans pass**: välj veckodag (mån–sön) och bygg ett pass av övningar.
- Tid per övning (förvald, kan justeras med − / +) och **total tid** för passet.
- Fördelning per kategori (stapel) så du ser balansen i passet.
- Ändra ordning, ta bort, anteckningar, kopiera passet som text, skriv ut,
  kopiera ett pass till en annan dag.
- **Markera genomfört** per pass, och "Ny vecka" för att nollställa markeringarna.
- Sparas i `localStorage` – alltså bara på den enhet du använder.

## Lägga till övningar

Öppna `index.html` och leta upp `const exercises = [`. Kopiera ett block:

```js
{ id:"min-ovning", category:"boll", name:"Min övning", minutes:8,
  desc:"Hur övningen går till.",
  tip:"Ett coachtips.", gear:"Koner, bollar" },
```

- `id` måste vara unikt och ska inte ändras senare (sparade pass pekar på det).
- `category` är en av nycklarna i `categories` (uppvarmning, boll, passning,
  skott, fys, styrka, spel, avslutning). Nya kategorier läggs till där.

## Publicera på GitHub Pages

1. Skapa ett nytt repo och lägg filerna i den här mappen i repots rot.
2. Settings → Pages → Deploy from branch → `main` / root.
3. Öppna sidan i mobilen och välj "Lägg till på hemskärmen".

Förhandsgranska lokalt:

```
python3 -m http.server 8000
```

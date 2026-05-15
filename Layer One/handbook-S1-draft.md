# Draft: Session 1 — Terminál, Hello World, struktura projektu

> **Pozn.:** Tohle je AI draft. Tvůj úkol je přečíst, pochopit a **přepsat vlastními slovy** do `Layer One/README.md`. Pak tenhle soubor smaž.

---

## O čem Session 1 byla

První session akademie. Cíl: dostat se z nuly do bodu, kdy v terminálu spustíš svůj první program. Praktická část: založení pracovní složky, naklonování repa z GitHubu, otevření ve VS Code, napsání `Console.WriteLine("2 + 2 = 4")` v Calculatoru, spuštění přes `dotnet run`.

Layer 1 má dva paralelní projekty:

- **Calculator** — společný, píše se na sessions s Martinem.
- **PandaNursery** — tvůj osobní projekt, na něm pracuješ offline mezi sessions.

---

## Klíčové koncepty

### Terminál (zsh na macOS)

Terminál je textové okno, kde **píšeš příkazy** programům. „Terminál", „konzole" a „command line" je v podstatě totéž. Na Macu se hodí iTerm2 místo defaultní Terminal.app, ale není to nutné.

**Pravidlo č. 1:** Terminál neumí teleportovat. Když napíšeš jen cestu (`/Users/.../member-terka`), pokouší se ji spustit jako program. Pro navigaci a spouštění **potřebuješ příkaz**.

**Základní příkazy:**

| Příkaz | Co dělá |
|---|---|
| `pwd` | „print working directory" — kde právě jsem |
| `ls` | seznam souborů a složek tady |
| `cd <cesta>` | „change directory" — jdi do té složky |
| `cd ..` | jdi o úroveň výš |
| `clear` | vyčisti obrazovku (historie zůstane, jen scrolluje pryč) |

**Tipy do svalové paměti:**
- Mezi `cd` a cestou je **mezera**: `cd /Users/...`, ne `cd/Users/...`.
- **Tab autocomplete:** napiš začátek a stiskni Tab, terminál ti dopne.
- **Šipka nahoru/dolů:** projíždí historii dřívějších příkazů.
- **Drag & drop:** napiš `cd ` (s mezerou) a přetáhni složku z Finderu — cesta se vloží.
- **Ctrl + C** ukončí běžící program (NE Cmd + C — to je copy).

### `dotnet run --project` — jak spustit .NET aplikaci

```bash
dotnet run --project src/PandaNursery
```

Rozklad:
- `dotnet` — program, který umí pracovat s .NET projekty.
- `run` — subcommand „spusť".
- `--project` — „a teď ti řeknu, který".
- `src/PandaNursery` — cesta ke složce, kde je `.csproj` soubor.

**Důležité:** příkaz **musí začínat slovem `dotnet`**. Samotné `run --project ...` nebo `donet` (překlep) terminál nezná → `command not found`.

### Co je v souboru `Program.cs`

```csharp
namespace PandaNursery;

class Program
{
    static void Main(string[] args)
    {
        // tvůj kód
    }
}
```

**Vrstvy:**

- **`namespace PandaNursery;`** — „škatulka", do které kód patří. Jméno typicky odpovídá projektu.
- **`class Program`** — třída, kontejner pro kód. V Layer 1 jí budeš jen psát kód, k objektovému programování se dostaneš později.
- **`static void Main(string[] args)`** — **entry point**, místo, kde .NET začíná spouštět kód. Tahle hlavička je pevně daná, neměníš ji. Píšeš dovnitř těch chlupatých závorek `{ }`.
- **Tělo `Main`** — všechno, co bude program dělat. Řádek po řádku, shora dolů.

### `Console.WriteLine` — výpis do konzole

```csharp
Console.WriteLine("Hello World");
```

- `Console` — třída z .NET na práci s konzolí.
- `WriteLine` — metoda, která text **vypíše a odřádkuje**.
- Text se dává **do uvozovek** `"…"`.
- Každý příkaz končí **středníkem** `;`.

Pokud chceš jen vypsat bez odřádkování, je `Console.Write` (bez „Line").

### `Console.ReadKey` — počkej na klávesu

```csharp
Console.ReadKey();
```

Zastaví program, dokud uživatel nestiskne libovolnou klávesu. Hodí se na konec programu, ať se okno nezavře dřív, než si výpis stihneš přečíst. V `dotnet run` z terminálu ho moc nepotřebuješ (terminál se nezavírá), ale ve VS Code Run tlačítku se hodí.

### Pravidla syntaxe, na kterých se začátečníci pálí

1. **Středník `;`** na konci každého příkazu. Bez něj → `error CS1002: Očekával se středník`.
2. **Case sensitivity:** `Console` ≠ `console`, `WriteLine` ≠ `writeline`. Velké/malé písmeno hraje roli.
3. **Uvozovky** kolem textu: `"Ahoj"`, ne `Ahoj` ani `'Ahoj'` (jednoduché uvozovky jsou pro znaky, ne řetězce).
4. **Chlupaté závorky `{ }`** označují blok kódu. Otevírající a uzavírající musí být v páru.
5. **Komentáře** `//` — řádky začínající `//` program ignoruje, jsou pro čtenáře:
   ```csharp
   // tohle je komentář, kompilátor ho přeskočí
   Console.WriteLine("Ahoj"); // tahle část za příkazem taky
   ```

### Chyby vs warnings

- **Error (chyba)** — kompilátor nezvládne kód sestavit. **Musíš opravit.** Příklad: `error CS1002: Očekával se středník`.
- **Warning (varování)** — „nelíbí se mi to, ale spustím to". Kód běží. Příklad: `warning CS8600` u `Console.ReadLine()` — že může vrátit `null` a tvůj kód s tím nepočítá. V Layer 1 to ignoruj, vrátíme se k tomu v S8 (try-catch).

**Mini pravidlo:** Vždycky čti **první chybu** v hlášení, ne tu poslední. Jedna chyba často vyrobí kaskádu dalších.

### Git — verzování v jedné větě

Git = nástroj na **checkpointování** kódu. Každý **commit** je checkpoint, ke kterému se můžeš vrátit. **Push** pošle tvoje commity na GitHub, **pull** stáhne cizí. V Layer 1 se commituje **přímo na `main`**, žádné branche.

Detailněji probereme v S2, kde se commit + push budou opakovat.

### VS Code — kde co je

- **Solution Explorer (levý panel)** — strom souborů projektu. Rozbal `src` → projekt → `Program.cs`.
- **Run/Debug tlačítko** — vpravo nahoře, spustí projekt. Stejné jako `dotnet run`, ale pomalejší (debug mód) — víc o tom v S5 (breakpoints).
- **Cmd + S** — uložit soubor. **Bez uložení tvoje změny do `dotnet run` nedorazí.**
- **Cmd + Shift + V** — náhled markdown souboru (vrátíme se v handbook práci).
- **Terminál v VS Code:** menu **Terminal → New Terminal** — otevře terminál hned uvnitř editoru.
- **Otevřít projekt z terminálu:** `code .` (tečka = aktuální složka). Pokud `code` nefunguje (`command not found`), použij `open -a "Visual Studio Code" .` jako rychlou okliku.

---

## Acceptance criteria S1 (ticket #1)

- [x] `src/PandaNursery/Program.cs` obsahuje `Console.WriteLine` s vlastní zprávou
- [x] Program se úspěšně spustí

Tvoje řešení: `Console.WriteLine("Ahoj, Vítej v Pandím světě");` — funguje.

---

## Co se na sessions probíralo, ale teď to ještě nepotřebuješ

- **Debug vs release mód spouštění** — proč VS Code Run běží pomaleji než `dotnet run` v terminálu. Vrátíme se k tomu v S5 (breakpoints).
- **Vícebarevný výpis** (`Console.ForegroundColor`, `BackgroundColor`, `ResetColor`) — bonus challenge. Není nutný pro ticket, ale tvoje stávající poznámky to už mají, takže máš s tím zkušenost.

---

## Index konceptů (do hlavního handbooku)

- terminál (cd, ls, pwd) → S1
- dotnet run --project → S1
- namespace, class, Main → S1
- Console.WriteLine → S1
- Console.ReadKey → S1
- středník, chlupaté závorky, case sensitivity → S1
- komentáře `//` → S1
- error vs warning → S1
- git (úvod) → S1, detail v S2

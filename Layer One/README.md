### Poznámky z první lekce  
#### terminálové příkazy
**clear** vymaže historii 
**cd** change directory 
**cd ..** vrátit se zpátky o úroveň výše ve složce
**ls** ověří co v tom daném directory je 
**git clone a odkaz https://github.git** naklonuje do složky, vždycky to musí končit .git
**code .** - otevři aktuální lokaci 
**dotnet run --project *(src/Calculator)****
Psát text vždy do **"text"**
Vždy kód ve visual studio uložit **commandS**
Šipka nahoru/dolů - znovu opíše terminálový příkaz - cykluješ mezi příkazy v historii
Nelze upravovat příkazy myší, musíš vždy popojet šipečkama doleva/doprava
**Chlupaté závorky {}** vždy odsazovat na další řádek 
Když píšu text written.line - dát TAB a odsadit text 
**Command Shift v** udělá normální zobrazení markdownu
**Command C** zruší příkaz v terminálu 

#### Úkol z první lekce: S1 
class Program
{
    static void Main(string[] args)
    {
        Console.ForegroundColor=ConsoleColor.DarkMagenta;
        Console.BackgroundColor=ConsoleColor.DarkYellow;
        Console.WriteLine("Vítej v Pandalandu, kde lidé mají rádi Pandy");
        Console.WriteLine("A taky růžovou");
        Console.BackgroundColor=ConsoleColor.Black;
        Console.ResetColor();

    }
}


#### Kódíčky
Console.Writeline ("Hello World");
Console.ReadKey (); tzn. že musíš stisknout libovolnou klávesnici pro pokračování 
Console.ForegroundColor = ConsoleColor.Red;
Console.WriteLine("Chyba: Soubor nenalezen!");
Console.ResetColor(); // vrátí původní barvy
Console.BackgroundColor=ConsoleColor.Gray;
- vždy resetovat color, ať to nedělá neplechu a nestane se to statickým  
## Poznámky z první lekce  
Wrapper postavený nad umělou inteligencí funguje na základě systémových promptů (chovej se jako mentor např.) a bere si data z velkých LLM modelů 

#### terminálové příkazy
**commit** - check point, každý commit musí mít message co v rámci toho bylo udělaný. 

**git status** 

terezamullerova@mac CodeToGodmode % /Users/terezamullerova/Desktop/CodeToGodmode/member-terka
zsh: permission denied: /Users/terezamullerova/Desktop/CodeToGodmode/member-terka
terezamullerova@mac CodeToGodmode % cd member-terka
terezamullerova@mac member-terka % git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   src/Calculator/Program.cs
	modified:   src/PandaNursery/Program.cs

git status mi vypsal všechny změny na Calculatoru i na PandaNursery a git add přidám jen vybranou změnu git add . přidám všechny změny

no changes added to commit (use "git add" and/or "git commit -a")
terezamullerova@mac member-terka %

**git add** vypsat jaké změny (src/PandaNursery/Program.cs)
**git add .** přidáš všechny změny, dáváš je do stage (všechny změny)

**git commit -a** git Příkaz git commit -a dělá dvě věci najednou:

Automaticky přidá do stage všechny změny — nemusíš psát git add zvlášť
Commitne je — vytvoří commit se zprávou

Prakticky
Máš soubor Calculator.cs, který jsi změnil. Místo:

git add Calculator.cs
git commit -m "Fix division method"


Stačí:

git commit -a -m "Fix division method"


Nebo zkráceno (mnemotechnika: all + message):

git commit -am "Fix division method"


Důležité omezení
git commit -a přidá jen existující soubory, které git už sleduje. Nové soubory vůbec nezachytí — ty musíš přidat přes git add ručně.

Příklad
git commit -a -m "Update existing files"
# ✅ Commitne změny v Calculator.cs, Program.cs atd.
# ❌ Ale ignores nový soubor Utils.cs, co jsi právě vytvořil


Praktická rada
Pro začátečníky je bezpečnější psát příkazy zvlášť:

git add .              # přidej všechno (i nové soubory)
git commit -m "..."    # commitni

terezamullerova@mac member-terka % git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   src/Calculator/Program.cs
	modified:   src/PandaNursery/Program.cs

no changes added to commit (use "git add" and/or "git commit -a")
terezamullerova@mac member-terka % git add src/PandaNursery/Program.cs
terezamullerova@mac member-terka % git add .
terezamullerova@mac member-terka % git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   src/Calculator/Program.cs
	modified:   src/PandaNursery/Program.cs
**git commit -m "Text"**
terezamullerova@mac member-terka % git commit -m "Změnila si pozadí a uvítací hlášku"
[main c29a209] Změnila si pozadí a uvítací hlášku
 Committer: Tereza Müllerová <terezamullerova@mac.home>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 2 files changed, 21 insertions(+), 3 deletions(-)
terezamullerova@mac member-terka % git log --oneline

**git log --oneline** stav commitů se zprávou, kterou sme napsali do commit message -m

c29a209 (HEAD -> main) Změnila si pozadí a uvítací hlášku
a307c83 (origin/main, origin/HEAD) Add README for PandaNursery project
db92ae8 Initial: member repo scaffolded with Calculator + personal project
terezamullerova@mac member-terka % git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
terezamullerova@mac member-terka %

**git push** pushnu to na github 

#### Martin Calculator
class Program
{
    static void Main(string[] args)
    {
        // Prázdný řádek nahoře
        Console.WriteLine();

        // Horní oddělovač — tyrkysová
        Console.ForegroundColor = ConsoleColor.Cyan;
        Console.WriteLine("━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━");
        Console.WriteLine();

        // Hlavní titulek — žlutá
        Console.ForegroundColor = ConsoleColor.Yellow;
        Console.WriteLine("          MARTIN'S CALCULATOR");

        // Podtitul — zelená
        Console.ForegroundColor = ConsoleColor.Green;
        Console.WriteLine("             CTGM Academy");

        // Verze — tmavě šedá
        Console.ForegroundColor = ConsoleColor.DarkGray;
        Console.WriteLine("                 v1.0");
        Console.WriteLine();

        // Dolní oddělovač — tyrkysová
        Console.ForegroundColor = ConsoleColor.Cyan;
        Console.WriteLine("━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━");

        Console.ForegroundColor = ConsoleColor.White;
        Console.WriteLine();
        Console.WriteLine("2 + 2 = 4 ");
        Console.WriteLine();
        Console.ResetColor();

        // Prompt pro ukončení — tmavě šedá
        Console.ForegroundColor = ConsoleColor.DarkGray;
        Console.WriteLine("Stiskni libovolnou klávesu pro ukončení...");
        Console.ResetColor();

        // Pauza — aby se aplikace nezavřela okamžitě
        Console.ReadKey();
    }
}

#### Zlodějina
v Repu si zkopíruješ kód, dáš si tam git clone + url a uložit do složky member-terka

Kontrola: 
Git status - řekne, že já sem nedělala žádné změny 
**Git fetch** - zobrazí delty, načte změny z remotu do lokálu 
**git log** --oneline - zobrazí ty změny 
**git push** vezme si všechny změny z repa 
**git add .** přidá na git 
**git status** řekne mi status

*Push na github chce občas mail a user name*
*git config --global user.email "you@example.com"
git config --global user.name "Your Name"

#### S2 - Datové typy, Terka Samouk

Pravidlo z S1: každý příkaz v C# končí středníkem. To platí i pro deklaraci
  proměnné (čili „rezervaci paměti" pod nějakým jménem).

  Mezitím — krátký výlet do S2: co jsi vlastně napsala

  Tohle:
  string jmenoPandy;
  říká kompilátoru: „vyhraď mi v paměti místo na text (string), říkej mu
  jmenoPandy."

  V paměti pak vznikne prázdná škatulka se jmenovkou jmenoPandy, do které ještě
  nic není uloženo. Naplníš ji později (např. jmenoPandy = Console.ReadLine(); —
  to bude další krok).

  Rozklad jednoho řádku:
  string   jmenoPandy   ;
    ↑          ↑        ↑
  typ       jméno    konec příkazu
         proměnné

  - Typ — jaký druh dat tam půjde:
    - string = text (sekvence znaků v uvozovkách)
    - int = celé číslo
    - float = desetinné číslo (přibližně 7 desetinných míst přesnosti)
    - bool = pravda/nepravda
  - Jméno — jak budeš proměnnou v kódu volat. Konvence v C# = camelCase: první
  písmeno malé, další slova s velkým: jmenoPandy, vahaKg, textovyVstup.
  - Středník — konec příkazu.

  Můžeš deklarovat a rovnou přiřadit:
  string pozdrav = "Ahoj";   // deklarace + inicializace najednou

  Nebo nejdřív deklarovat a později přiřadit:
  string pozdrav;            // jen deklarace, "škatulka" prázdná
  pozdrav = "Ahoj";          // přiřazení hodnoty

  Pochvala mezi řečí

  To, že sis kód rozdělila komentáři // Pozn. S1 a //S2:, je výborný zvyk. Budoucí
   ty si to ocení.

   Den 1 — co jsme spolu prošli

  Terminál a navigace v projektu

  - cd = change directory, ls = list, pwd = print working directory
  - Mezi cd a cestou je mezera (sežrala tě jednou)
  - Tab autocomplete, šipky v historii, drag & drop složky do terminálu
  - Terminál neumí teleportovat — samotná cesta není příkaz
  - Ctrl + C ukončí běžící program (NE Cmd+C)

  .NET projekt a první spuštění

  - dotnet run --project src/PandaNursery — celý prefix dotnet je povinný
  - donet (překlep) → command not found (našel jsi i toto)
  - Otevření VS Code z terminálu: open -a "Visual Studio Code" . (oklika),
  případně code . po nastavení Shell Command

  Struktura Program.cs (S1)

  namespace PandaNursery;     // škatulka
  class Program               // kontejner pro kód
  {
      static void Main(...)   // entry point — kde to začíná
      {
          // tvůj kód
      }
  }

  - Console.WriteLine("text") — výpis + odřádkování
  - Console.ReadKey() — počká na libovolnou klávesu
  - Console.ReadLine() — počká na Enter, vrátí string
  - Každý příkaz končí středníkem ;
  - C# je case-sensitive (Console ≠ console)

  Proměnné a typy (S2)

  - Deklarace: typ jméno; (např. string jmenoPandy;)
  - Typy: string (text), int (celé číslo), float (desetinné), bool (true/false)
  - camelCase konvence: jmenoPandy, vahaKg, textovyVstup
  - Přiřazení: proměnná = hodnota;
  - Deklarace bez přiřazení = prázdná škatulka, do které nelze sahat dokud se
  nenaplní

  Vstup od uživatele a parsování

  - Console.ReadLine() vrací VŽDY string, i kdyby uživatel napsal číslo
  - Pro číslo musíš parsovat: float.Parse(textovyVstup)
  - Pomocná škatulka textovyVstup = přestupní stanice mezi string a float

  Locale a manipulace se stringy

  To byla dnešní nejtěžší dovednost. Cesta:

  1. Locale problém — český systém čeká 50,5 (čárka), 50.5 (tečka) spadne s
  FormatException
  2. Stringy jsou immutable — Replace a Trim vrací nový string, musíš si ho uložit
   zpátky
  3. string.Replace("co", "čím") — najít/nahradit
  4. string.Trim() — odstraní whitespace jen z okrajů, NE písmenka uvnitř
  5. string.ToLower() — celý string malými písmeny
  6. Method chaining — .Replace(...).Replace(...).Trim() zřetězí volání

  Finální robustní řádek, co jsi napsala:
  textovyVstup = textovyVstup.ToLower()
                             .Replace(".", ",")
                             .Replace("kg", "")
                             .Trim();

  Akceptuje 50, 50,5, 50.5, 50 kg, 50,5kg, 50 KG, 50.5 Kg…

  String interpolace

  Console.WriteLine($"Tvoje panda: {jmenoPandy}, váha: {vahaKg} kg byla
  zaregistrována");
  - $ před "…" zapne interpolaci
  - {proměnná} se za běhu nahradí hodnotou

  Chyby — dva druhy

  - Compile-time (např. CS1002 chybí středník) — program vůbec nespustí,
  kompilátor odmítne sestavit
  - Runtime (např. FormatException) — program běžel a spadl na konkrétním vstupu

  Pravidlo: vždycky čti první chybu, ne poslední — jedna chyba často vyrobí
  kaskádu dalších.

  Limity Replace přístupu

  - Replace umí jen přesné shody, co jsi mu řekla najít
  - Pro vstupy jako kd, padesát, prázdný řetězec → spadne to
  - Robustní řešení: try-catch nebo float.TryParse → S8

  Git workflow

  - git status — co je modifikované
  - git add <konkrétní soubor> — do staging (NE git add ., vleze ti tam i bordel)
  - git commit -m "Session X: popis CO" — checkpoint (NE commitni ani prosím
  commit)
  - git push — nahraj na GitHub
  - Cache soubory (.lscache) se commitují, když dáš git add . — Martin to ale v
  Layer 1 toleruje

#### Základní datové typy 
Číselné typy
    **int** - celá čísla
    int sebere 4byty v operační paměti - to kolik to bere paměti se nemusí řešit C# je high level language 
    **float** (8 desetinných míst)/ double(16 desetinných míst - větší hodnota) - desetinná čísla 
Text
    **string** - text "Ahoj"
    string uvitaciZprava; - rezervuješ si operační paměť - přiřazení hodnoty do proměnné 
Logická hodnota 
    **bool** - pravda/nepravda (true, false) 0 false/vypnuto nebo 1 true/zapnuto
Kolekce 
    **array/list** - seznam hodnot 
    **object/dicstionary** data ve formátu klíč-hodnota

**String interpolation** - způsob jak vkládat proměnné přímo do textu (stringu)
**Console.Writeline ($"První číslo: {prvniCislo}. Druhé číslo: {druheCislo}.") Výsledek součtu: {výsledek};

Systém pojmenování proměnných - **camel case** vždy bez mezer, jedno slovo složené z více slov - uvitaciZprava, druheCislo, ty konvence v prográmku určují, jak by měly být pojmenované proměnné 

string uvitaciZprava = "Prdel";
        int prvniCislo = 5;
        int druheCislo = 500;
        int vysledek = 100;

        Console.WriteLine (uvitaciZprava);
        Console.WriteLine ($"První číslo: {prvniCislo}. Druhé číslo: {druheCislo}. Výsledek součtu: {vysledek}");
        Console.ReadKey();

Hodnoty výše jsou natvrdo

**Console.ReadLine();** pozoruje co uživatel píše do té doby než přestane psát 

static void Main(string[] args)
    {
        // Tvůj první program — na první session přepíšeš na "2 + 2 = 4"
        string uvitaciZprava = "Prdel";
        int prvniCislo = 5;
        int druheCislo = 500;
        int vysledek = 100;

        Console.WriteLine (uvitaciZprava);
        Console.WriteLine ($"První číslo: {prvniCislo}. Druhé číslo: {druheCislo}. Výsledek součtu: {vysledek}");
        Console.ReadKey();

// Tvůj první program — na první session přepíšeš na "2 + 2 = 4"
        string jmenoUzivatele;
        prvniCislo = 10;
        druheCisglo = 5000;
        vysledek = 10;
       
        Console.WriteLine ($"První číslo: {prvniCislo}. Druhé číslo: {druheCislo}. Výsledek součtu: {vysledek}");
        
        Console.WriteLine ("Řekni mi jméno a dej Enter");
        jmenoUzivatele = Console.ReadLine();
        Console.WriteLine ($"Ahoj uživateli {jmenoUzivatele}, vítej v kalkulačce");
        Console.ReadKey();

        Console.WriteLine("Hello from Martin's Calculator!");
        Console.ForegroundColor=ConsoleColor.Green;
        Console.WriteLine("2+2=4");
        Console.ResetColor();
        Console.ReadKey();
        Console.ForegroundColor=ConsoleColor.Red;
        Console.WriteLine("Martin říká, že 2+2=5, má to trochu pomíchané");
        Console.ResetColor();
        
    }
} 
Parse je převod mezi datovými typy

Upravit bordel:   // Tvůj první program — na první session přepíšeš na "2 + 2 = 4"
        string uvitaciZprava = "Prdel";
        float prvniCislo = 5;
        float druheCislo = 500;
        float vysledek = 100;

        Console.WriteLine (uvitaciZprava);
        Console.WriteLine ($"První číslo: {prvniCislo}. Druhé číslo: {druheCislo}. Výsledek součtu: {vysledek}");
        Console.ReadKey();

// Tvůj první program — na první session přepíšeš na "2 + 2 = 4"
        string jmenoUzivatele;
        prvniCislo = 10;
        druheCislo = 5000;
        vysledek = 10;
       
      
        Console.WriteLine ("Řekni mi jméno a dej Enter");

        Console.WriteLine ("Řekni mi jméno a dej Enter");
        jmenoUzivatele = Console.ReadLine();
        Console.WriteLine ($"Ahoj uživateli {jmenoUzivatele}, vítej v kalkulačce");
        Console.ReadKey();

        string textCislo = "1";
        int intCislo = 1;
        Console.WriteLine (textCislo + textCislo);
        Console.WriteLine (intCislo + intCislo);
    
        Console.WriteLine ($"První číslo: {prvniCislo}. Druhé číslo: {druheCislo}. Výsledek součtu: {vysledek}");
        string textoveCislo;
        textoveCislo = Console.ReadLine();
        prvniCislo = float.Parse(textoveCislo);
        Console.WriteLine("Řekni mi druhé číslo a Enter!");
        textoveCislo = Console.ReadLine();
        druheCislo = float.Parse (textoveCislo);
        vysledek = prvniCislo + druheCislo;

        Console.WriteLine("Hello from Martin's Calculator!");
        Console.ForegroundColor=ConsoleColor.Green;
        Console.WriteLine("2+2=4");
        Console.ResetColor();
        Console.ReadKey();
        Console.ForegroundColor=ConsoleColor.Red;
        Console.WriteLine("Martin říká, že 2+2=5, má to trochu pomíchané");
        Console.ResetColor();
        
    }

static void Main(string[] args)
    {
        // Tvůj první program — na první session přepíšeš na "2 + 2 = 4"
        string uvitaciZprava = "Prdel";
        float prvniCislo = 5;
        float druheCislo = 500;
        float vysledek = 100;

        Console.WriteLine (uvitaciZprava);
        Console.WriteLine ($"První číslo: {prvniCislo}. Druhé číslo: {druheCislo}. Výsledek součtu: {vysledek}");
        Console.ReadKey();

// Tvůj první program — na první session přepíšeš na "2 + 2 = 4"
        string jmenoUzivatele;
        prvniCislo = 10;
        druheCislo = 5000;
        vysledek = 10;
       
      
        Console.WriteLine ("Řekni mi jméno a dej Enter");

        Console.WriteLine ("Řekni mi jméno a dej Enter");
        jmenoUzivatele = Console.ReadLine();
        Console.WriteLine ($"Ahoj uživateli {jmenoUzivatele}, vítej v kalkulačce");
        Console.ReadKey();

        string textCislo = "1";
        int intCislo = 1;
        Console.WriteLine (textCislo + textCislo);
        Console.WriteLine (intCislo + intCislo);
    
        Console.WriteLine ($"První číslo: {prvniCislo}. Druhé číslo: {druheCislo}. Výsledek součtu: {vysledek}");
        string textoveCislo;
        textoveCislo = Console.ReadLine();
        prvniCislo = float.Parse(textoveCislo);
        Console.WriteLine("Řekni mi druhé číslo a Enter!");
        textoveCislo = Console.ReadLine();
        druheCislo = float.Parse (textoveCislo);
        vysledek = prvniCislo + druheCislo;

        Console.WriteLine("Hello from Martin's Calculator!");
        Console.ForegroundColor=ConsoleColor.Green;
        Console.WriteLine("2+2=4");
        Console.ResetColor();
        Console.ReadKey();
        Console.ForegroundColor=ConsoleColor.Red;
        Console.WriteLine("Martin říká, že 2+2=5, má to trochu pomíchané");
        Console.ResetColor();
        
    }
} 

### Session 3 - Enum 

class Program
{
    static void Main(string[] args)
    {
        string choiceText;
        int choiceNumber;
        Operation choice;
    
        Console.WriteLine("Vyber si operaci a dej enter");
        Console.WriteLine("Sčítání - 0");
        Console.WriteLine("Odečítání - 1");
        Console.WriteLine("Násobení -2");
        Console.WriteLine("Dělení - 3");
        choiceText = Console.ReadLine();
        choiceNumber = int.Parse(choiceText);
        choice = (Operation)choiceNumber; 

        Console.WriteLine($"Vybral sis operaci číslo {choice}");

    }
}

 static void Main(string[] args)
    {
        Console.WriteLine("Má Terka žízeň?");
        string zizen = Console.ReadLine();
        zizen = zizen.ToLower();
        Console.WriteLine($"Žízeň = {zizen}");
        if (zizen == "ano")
        {
            Console.WriteLine($"Terka si dá drinčík");
        }
        else if (zizen == "trochu")
        {
            Console.WriteLine("Terka neví co chce");
        }
        else
        {
            Console.WriteLine("Terka si nedá žádnej drinčák!");
        }
        Console.ReadKey();

Session 4 using System.Security.Cryptography;

namespace Calculator;

enum Operation
{
    Add,//0
    Substract,//1
    Multiply,//2
    Divide,//3
}
class Program
{
    static void Main(string[] args)
    { 
        string textInput;
        int choiceNumber;
        Operation choice;

        float firstNumber;
        float secondNumber;
        float result = 0F;
    
        Console.WriteLine("Vyber si operaci a dej enter");
        Console.WriteLine("Sčítání - 0");
        Console.WriteLine("Odečítání - 1");
        Console.WriteLine("Násobení -2");
        Console.WriteLine("Dělení - 3");
        textInput = Console.ReadLine();
        choiceNumber = int.Parse(textInput);

        if (choiceNumber < 1 || choiceNumber > 4)
        {
            Console.WriteLine("Napsal si nahovno číslo");
            return;
        }
        
        choice = (Operation)(choiceNumber - 1); 

        Console.WriteLine($"Vybral sis operaci číslo {choice}");
    
        Console.WriteLine("Napiš první číslo a dej Enter");
        textInput = Console.ReadLine();
        firstNumber = float.Parse(textInput);
        Console.WriteLine("Napiš druhé číslo a dej Enter");
        textInput = Console.ReadLine();
        secondNumber = float.Parse(textInput);
    

        Console.WriteLine($"Vybral sis operaci {choice} | První číslo: {firstNumber} | Druhé číslo: {secondNumber}");
        if (choice == Operation.Add)
        {
            result = firstNumber + secondNumber;
        }
        else if (choice == Operation.Substract)
        {
            result = firstNumber - secondNumber;
        }
        else if (choice == Operation.Multiply)
        {
            result = firstNumber * secondNumber;
        }
        else if (choice == Operation.Divide)
        {
            if (secondNumber !=0)
            {
                result = firstNumber / secondNumber;
            }
            else
            {
                Console.WriteLine("Nulou se nedá dělit");
            }
        }
        else
            {
                Console.WriteLine("Nulou se nedá dělit");
            }

        Console.WriteLine($"Výsledek: {result}");
    
    }
}

#### Session 4
switch (choice)
        {
            case Operation.Add:
            {
                result = firstNumber + secondNumber;
                break;
            }
        }
switch (choice)
        {
            case Operation.Multiply:
            {
                result = firstNumber / secondNumber;
                break;
            }
        }

Komentáře cmd K C a odkomentovat cmd K U
C je jako comment a U je jako uncomment

### Martinovo cykly 
Chce říct uživateli, že je debil a neumí to ovládat 5x

For cyklus vezme kus kódu a zopakuje ho 
iterační proměnná for (int i - 0)
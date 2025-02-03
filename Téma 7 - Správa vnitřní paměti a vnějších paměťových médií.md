### Pojmy a zkratky
Úložiště - perzistentní úložiště dat (pevný disk, SSD, atd.)
Paměť - operační paměť (RAM)
BSOD - Blue screen of death
UEFI - United extensible firmware interface
GUI - graphic user interface (grafické rozhraní)
CLI - command line interface (textové rozhraní)
## Vysvětlete roli správce **vnitřní paměti** v operačním systému
Správce paměti je část operačního systému, která přiděluje a uvolňuje paměť běžícím procesům. Také spravuje přístup k různým částem paměti (např. pokud program zasáhne do paměti, kterou používá Windows, dostaneme BSOD). Špatně fungující správce paměti znamená nestabilitu OS a může být velkou bezpečnostní hrozbou. Vede také záznam o tom, který proces má přiřazené jaké místo v paměti.
## Objasněte pojem reálná metoda přidělování paměti, popište přidělování paměti metodou jednoduchého stránkování.
Stránkování je nejzákladnější metoda přidělení paměti, podporuje také virtuální paměť. Funguje na principu rozdělení paměti (fyzické i virtuální) na stejně velké bloky (tzv. stránky). Přesnou velikost jedné stránky určuje architektura (většinou 4096 bytů, ale může to být jakákoliv mocnina dvojky).

Alokace - přidělování stránek procesům bez nutnosti paměť fyzicky alokovat. Alokací nazýváme přesun dat z úložiště (pevný disk nebo ssd) do paměti (RAM)
## Vysvětlete pojem virtuální metoda přidělování paměti, popište přidělování paměti metodou stránkování na žádost
Paměť se stránkuje až když je potřeba. To znamená mnohem větší efektivitu v přidělování paměti. Bloky paměti nemusí být stejně velké.
### Virtuální paměť
Pokud máme v počítače nedostatek RAM, použije náš počítač část primárního disku. Toto může způsobovat záseky/pomalejší běh programů, protože i M.2 SDD je mnohem pomalejší než RAM.
## Popište strukturu disku MBR a GPT, způsob označení diskových oddílů v OS Windows a Linux
### Master Boot Record (MBR)
Moderní obdoba Boot sektoru na disketách. Metadata disku jsou vždy oddělené od dat a jsou umístěná na samém začátku disku. MBR také obsahuj tabulku rozdělení disku (disk můžeme rozdělit na oddíly (partition), které fungují jako samostatné disky). Pouze 32 bitová adresace, takže maximální velikost disku je 2^32.
## GUID Partition Table (GPT, nemyslím tu AI)
Nejčastější struktura disků. Je součástí standardu UEFI. Na rozdíl od MBR podporuje 64 bitovou adresaci, takže podporuje větší disky. Má větší boot sektor. 
Pro zpětnou kompatibilitu použijeme Protective MBR, které umožní starším systémům disk rozpoznat (má primární hlavičku GPT)
## Windows
Windows přiřazuje diskům a oddílům písmena od `C`. `C` je vyhrazeno pro primární disk s OS, `D` a dále mohou být libovolné disky. `A` a `B` jsou vyhrazeny pro diskety (zpětná kompatibilita s DOS)
### Linux (a macOS)
Linux zobrazuje celý počítač jako adresářový strom, takže připojené disky nalezneme v adresáři `/dev/` (např. `/dev/sda1`)
## Popište nástroje pro správu disků v grafickém a textovém rozhraní
### Správa disků v GUI
#### Nástroj správa disku (Windows)
Zabudovaný nástroj, který umožňuje měnit u disků základní parametry (např. oddíly, název atd.). Také umožňuje disk naformátovat.
#### Průzkumník souborů (Windows)
Neumožňuje pokročilejší funkce, spíše pro uživatelské použití
#### GParted (Linux)
Grafické rozhraní pro zprávu disků v GNOME. Celkem uživatelsky přívětivé
### Správa disků přes CLI
#### Fdisk (Linux)
Nástroj pro operace s disky. Umožňuje spravovat oddíly
#### Diskpart (Windows)
Umožňuje veškeré operace s disky pomocí příkazového řádku.
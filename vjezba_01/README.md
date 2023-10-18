# Vježba 1 - Upoznavanje s razvojnom okolinom, kompajliranje C++ programa, debugiranje

## **1. Upoznavanje s c/c++ jezikom**

C/C++ su moćni programski jezici s dugom i bogatom poviješću. C je stariji od C++-a i poznat je po svojoj učinkovitosti i sposobnosti bliske manipulacije hardvera. C++ je evoluirao iz C-a dodavši mu objektno orijentirane koncepte, čineći ga fleksibilnijim i omogućujući razvoj modernijih aplikacija
### 1.1 Tipovi podataka

U C/C++-u, tipovi podataka definiraju vrstu vrijednosti koje varijable mogu držati. Ovi jezici podržavaju širok spektar tipova, uključujući cjelobrojne, decimalne, znakovne, pokazivačke, i mnoge druge.

Primjeri tipova podataka u C++-u:
```cpp
int broj = 42;          // Cjelobrojni tip podataka
double decBroj = 3.14;  // Decimalni tip podataka
char znak = 'A';        // Znakovni tip podataka
```

Što ako želimo imati strukture koje u sebi mogu sadržavati više podataka, iste obrađivati, pamtiti i mijenjati stanja?
### 1.2 Objektno orijentirano programiranje

Odgovor na gore postavljeno pitanje je objektno orijentirano programiranje!

Objektno orijentirano programiranje (OOP) je paradigma programiranja koja se oslanja na koncept objekata. Objekti grupiraju podatke i povezane operacije (metode) koje rade nad tim podacima. C++ je snažan OOP jezik koji omogućava strukturiranje koda kroz klase i objekte.
#### 1.2.1 Što su metode?

Metode su funkcije koje su povezane s objektima. Svaki objekt klase može izvršavati metode povezane s tom klasom. Metode predstavljaju operacije koje se izvršavaju nad podacima objekta.

Primjer definicije klase s metodama u C++-u:
```cpp
#include <iostream>

class Automobil {
public:
    // Metoda za postavljanje brzine automobila
    void postaviBrzinu(int novaBrzina) {
        brzina = novaBrzina;
    }

    // Metoda za ispis trenutne brzine automobila
    void ispisiBrzinu() {
        std::cout << "Trenutna brzina automobila: " << brzina << " km/h" << std::endl;
    }

private:
    int brzina;
};

int main() {
    Automobil mojAuto;
    mojAuto.postaviBrzinu(60);
    mojAuto.ispisiBrzinu();  // Ispisuje "Trenutna brzina automobila: 60 km/h"

    return 0;
}
```

---
## **2. Visual Studio Code**

### 2.1 'Lightweight' IDE

Visual Studio Code je jednostavni (eng. lightweight) IDE u kojem možete pokretati sve što poželite, samo morate instalirati potrebne dodatke (eng. plugins).

```
💡 IDE (Integrated Development Environment) je skraćenica koja označava "Integrirano razvojno okruženje". To je softverski alatni skup koji pruža sveobuhvatno okruženje za programiranje, obično s nizom alata, značajki i resursa koji olakšavaju razvoj softvera. IDE integrira različite aspekte programiranja, uključujući uređivanje koda, debugiranje, izgradnju (build), upravljanje verzijama, i druge zadatke, sve unutar jednog korisničkog sučelja.
```

Za pokretanje `c++` programa potreban vam je dodatak: C/C++.

Uz njega slobodno instalirajte i 'C++ Intellisense' dodatak koji će vam olakšati programiranje jer vam daje prijedloge dok pišete kod, dapače, kad radite s objektima, javlja vam i koje varijable i metode taj objekt sadrži.
### 2.2 Prevođenje i povezivanje programa

Proces prevođenja i povezivanja programa, poznat i kao kompajliranje, ključan je korak u stvaranju izvršnog programa (`.exe` datoteke) iz izvornog koda napisanog na nekom programskom jeziku. 

Za potrebe vježbe je pripremljen mehanizam za prevođenje i pokretanje (skriven u `.vscode` mapi i `build.bat` datoteci). 

Proces prevođenja i povezivanja u `.exe` datoteku (build) se vrši pomoću prečaca: `CTRL` + `SHIFT` + `B`.

Ono što morate provjeriti prije no što pritisnete prečac kojim pozivate build vašeg programa je sljedeće:

Otvorite `build.bat` datoteku. U njoj se nalazi putanja na alat iz Visual Studia:
```cpp
call "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"
```

Provjerite je li na vašem računalu instalirana verzija Visual Studia koja se poziva u toj putanji. Ako nije, pronađite mjesto na kojeme se nalazi `VsDevCmd.bat` of verzije Visual Studia koji je instaliran na vašem računalu. Kopirajte putanju do tog alata i zalijepite je u `build.bat` datoteku.
### 2.3 Pokretanje programa

Program se pokreće nakon što se stvori `.exe` datoteka i to prečacom: `CTRL` + `F5`, ili izbornikom `Run` -> `Run Without Debugging`.

Ako je pokretanje uspješno, otvorit će vam se terminal i izvršit će se vaš program. 

```
💡 Imajte na umu da terminal zatvorite kad završite s proučavanjem ispisa. U suprotnom će vam ostati otvoreno previše prozora te u jednom trenutku više nećete moći pokretati vaš program.
```

Ako je pokretanje bilo neuspješno, u terminalu u VS Code-u će vam se ispisat informacije o grškama koje trebate otkloniti.

Proces otklanjanja grešaka se naziva debugging!
### 2.4 Debugging (ž. debugiranje)

Proces debugiranja je pronalaženje grešaka u vašem kodu. One mogu biti očite (kompajler vam ih javlja prilikom buildanja vašeg programa) ili manje očite (curenje memorije, opadanje performansi itd.).

Većina vaših programa koji budu imali greške će rezultarati ispisom istih u terminalu VS Code-a prilikom buildanja koda. Pomno porčitajte što vam kompajler govori te ispravite iste.

```
💡 U VS Code-u imate i izbornik 'Problems' na kojem će vam se nalaziti popis vaših grešaka i prije nego pokrenete postupak buildanja.
```

Neke greške će bit manje očite. Program će se uspješno izbuildati, ali nećete dobiti željeni ispis ili rezultate. Tada ćete trebati kroz vaš kod prolaziti korak po korak. To možete učiniti tako da program pokrenete s debugiranjem: `Run` -> `Start Debugging`.

Kada program pokrenete s debugiranjem kroz kod ćete prolaziti korak po korak. Pojavit će vam se plutajući izbornik pomoću kojeg se krećete među koracima, a sa strane će vam se pojaviti prozorčić u kojem će biti prikazane sve vaše trenutne varijable (i objketi) i njihov sadržaj, pa čak i promjene njihovog sadržaja.
### 2.5 Česte pogreške

Najčešća greška koja će vam se na vježbama javljati je vezana uz buildanje i pokretanje vaših programa. Ona najstaje jer se nešto poremetilo u `build.bat` datoteci ili `.vscode` mapi. Kako biste izbjegli te greške, nakon što raspakirate materijale za vježbe u VS Code-u nemojte otvarati mapu `vjezbe_23_24` već unutarnju mapu `/vjezbe_23_24/vjezbe_23_24`.

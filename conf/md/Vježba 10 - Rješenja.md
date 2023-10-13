## **Zadatak 10.1**

### Korak 1:
**Opišite što program main radi:**
* Program stvara dinamičke objekte tipova `LP`, `CD`, i `DVD`, zatim poziva njihove `Ispisi` metode i na kraju dealocira dinamički alocirane objekte.

**Opišite kakvi su međusobni odnosi klasa `ploca`, `LP`, `CD`, i `DVD`:**
- `ploca` je apstraktna klasa koja ima čisto virtualnu funkciju `Ispisi`.
- `LP`, `CD`, i `DVD` su izvedene klase od `ploca` i implementiraju `Ispisi` funkciju. `LP` dodatno ima `RPM`, `CD` ima `RW`, a `DVD` ima `dvostrani` član.

**Koja funkcija temeljne klase je realizirana kao virtualna? Što znači da je to virtualna funkcija?**
* Funkcija `Ispisi` iz temeljne klase `ploca` je realizirana kao čisto virtualna funkcija. To znači da je ta funkcija definirana u temeljnoj klasi, ali je ostavljena bez implementacije (označena sa `= 0`). 
* Svaka izvedena klasa mora pružiti svoju implementaciju ove funkcije!

### Korak 2:
Promijenjeni `main` koristi pokazivače tipa `ploca` za pohranjivanje adresa objekata tipova `LP`, `CD`, i `DVD`, omogućujući korištenje polimorfizma.

**Je li program daje isti ispis, odnosno obavlja istu funkciju:**
* Da, program daje isti ispis. Ispisuje informacije o vinilu, CD-u i DVD-u koristeći polimorfizam jer se koristi niz pokazivača na `ploca`.

### Korak 3:
Razlika u deklaraciji i alociranju objekata je u tome što se u drugom koraku koriste pokazivači na baznu klasu `ploca`. U prvom koraku su korišteni pokazivači na izvedene klase `LP`, `CD`, i `DVD`.

### Korak 4:
Ne bi bilo moguće automatski pristupiti objektima pomoću petlje jer bi niz bio ograničen na specifične tipove (`LP`, `CD`, `DVD`), a polimorfizam ne bi bio moguć.

### Korak 5:
Funkcija `Ispisi` je deklarirana u temeljnoj klasi `ploca` kao virtualna. Svaka izvedena klasa implementira vlastitu verziju ove funkcije. U prvoj petlji `A[i]->Ispisi();` koristi se polimorfizam - poziva se `Ispisi` funkcija specifična za svaki tip objekta. 

---

## **Zadatak 10.2**

### Korak 1:
Kreiranje datoteke `z1021.cpp` s klasama `clan_obitelji`, `roditelj` i `dijete`.

```cpp
#include <string>
#include <iostream>
using namespace std;

class clan_obitelji {
public:
    string ime_prezime;
    virtual void Ispisi(void) = 0;
};

class roditelj : public clan_obitelji {
public:
    int broj_djece;

    void Ispisi() {
        cout << "Roditelj: " << ime_prezime << ", Broj djece: " << broj_djece << endl;
    }
};

class dijete : public clan_obitelji {
public:
    bool kcer; // true ako je dijete ženskog spola

    void Ispisi() {
        cout << "Dijete: " << ime_prezime << ", Spol: " << (kcer ? "kćer" : "sin") << endl;
    }
};
```

**Glavni program:**
```cpp
int main() {
    roditelj* otac = new roditelj;
    dijete* dijete1 = new dijete;
    dijete* dijete2 = new dijete;

    otac->ime_prezime = "Otac Prvi";
    otac->broj_djece = 2;

    dijete1->ime_prezime = "Dijete Prvo";
    dijete1->kcer = false;

    dijete2->ime_prezime = "Dijete Drugo";
    dijete2->kcer = true;

    clan_obitelji* obitelj[3];
    obitelj[0] = otac;
    obitelj[1] = dijete1;
    obitelj[2] = dijete2;

    for (int i = 0; i < 3; i++)
        obitelj[i]->Ispisi();

    for (int i = 0; i < 3; i++)
        delete obitelj[i];

    return 0;
}
```

Ovdje smo stvorili dvije izvedene klase `roditelj` i `dijete` koje nasljeđuju apstraktnu klasu `clan_obitelji`. Svaka od njih implementira svoju verziju virtualne funkcije `Ispisi`. U glavnom programu stvaramo objekte tipa `roditelj` i `dijete`, dodjeljujemo im odgovarajuće vrijednosti, a zatim koristimo niz pokazivača na `clan_obitelji` za polimorfno upravljanje objektima. Nakon toga, objekti se dealociraju.

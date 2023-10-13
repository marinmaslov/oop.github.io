# Vježba 5 - Vrijeme trajanja i doseg varijabli, dinamička alokacija, nizovi

## 1. **Vrijeme trajanja i doseg varijabli:**

### 1.1 Globalne varijable
- **Vrijeme trajanja:** Tijekom cijelog programa.
- **Doseg:** Vidljive su svuda unutar programa.

```cpp
int globalnaVarijabla; // globalna varijabla

int main() {
    // globalnaVarijabla je vidljiva ovdje
}
```

### 1.2 Lokalne varijable
- **Vrijeme trajanja:** Unutar bloka gdje su deklarirane.
- **Doseg:** Vidljive samo unutar bloka.

```cpp
int main() {
    int lokalnaVarijabla; // lokalna varijabla

    // lokalnaVarijabla je vidljiva ovdje
}
```

### 1.3 Statičke varijable
- **Vrijeme trajanja:** Tijekom cijelog programa.
- **Doseg:** Ovisi o bloku u kojem su deklarirane.

```cpp
void funkcija() {
    static int statickaVarijabla; // statička varijabla unutar funkcije

    // statickaVarijabla je vidljiva ovdje, ali zadržava vrijednost između poziva funkcije
}
```

---

## 2. **Dinamička alokacija:**

### 2.1 Varijable
- **Alokacija dinamičkog prostora:**
    ```cpp
    int *pokazivac = new int; // alocira memoriju za jedan integer
    ```

- **Dealokacija dinamičkog prostora:**
    ```cpp
    delete pokazivac; // oslobađa alociranu memoriju
    ```

### 2.2 Objekti
Dinamička alokacija za objekte obično uključuje korištenje operatora `new` zajedno s konstruktorom klase. Evo primjera:

```cpp
#include <iostream>
using namespace std;

class Osoba {
private:
    string ime;
    int godine;

public:
    // Konstruktor
    Osoba(string i, int g) : ime(i), godine(g) {}

    // Članske funkcije
    void predstaviSe() {
        cout << "Moje ime je " << ime << " i imam " << godine << " godina." << endl;
    }
};

int main() {
    // Dinamička alokacija objekta klase Osoba
    Osoba *osoba1 = new Osoba("Ana", 25);

    // Poziv članske funkcije
    osoba1->predstaviSe();

    // Dealokacija dinamički alociranog objekta
    delete osoba1;

    return 0;
}
```

U ovom primjeru, `new` se koristi za dinamičku alokaciju objekta klase `Osoba`, a `delete` za njegovu dealokaciju. Važno je napomenuti da kad se koristi dinamička alokacija za objekte, trebate koristiti `delete` kako biste oslobodili alociranu memoriju nakon što završite s korištenjem objekta. Ovo je ključno kako biste izbjegli curenje memorije.

#### 2.2.1 Pozivanje metoda kod dinamički alociranih Objekata

Primjer:

```cpp
#include <iostream>
using namespace std;

class Osoba {
private:
    string ime;
    int godine;

public:
    // Konstruktor
    Osoba(string i, int g) : ime(i), godine(g) {}

    // Članske funkcije
    void predstaviSe() {
        cout << "Moje ime je " << ime << " i imam " << godine << " godina." << endl;
    }
};

int main() {
    // Dinamička alokacija objekta klase Osoba
    Osoba *osoba1 = new Osoba("Ana", 25);

    // Poziv metoda klase
    osoba1->predstaviSe();

    // Dealokacija dinamički alociranog objekta
    delete osoba1;

    return 0;
}
```

U ovom primjeru, `osoba1->predstaviSe();` poziva metodu `predstaviSe()` na dinamički alociranom objektu klase `Osoba`. Sintaksa `->` koristi se za pristup članovima dinamički alociranog objekta putem pokazivača. Ovo je ekvivalentno korištenju `(*osoba1).predstaviSe();`, ali `->` je češće korišteno u praksi jer je kraće i jasnije.

---

#### 3. **Nizovi:**

- **Deklaracija i inicijalizacija:**
    ```cpp
    int niz[5]; // deklaracija niza od 5 elemenata
    int niz2[] = {1, 2, 3, 4, 5}; // deklaracija i inicijalizacija niza
    ```

- **Pristup elementima niza:**
    ```cpp
    int vrijednost = niz[2]; // pristup trećem elementu niza (indeksiranje počinje od 0)
    ```

- **Dinamički niz:**
    ```cpp
    int *dinamickiNiz = new int[10]; // dinamička alokacija niza od 10 elemenata
    ```

- **Dealokacija dinamičkog niza:**
    ```cpp
    delete[] dinamickiNiz; // dealokacija dinamički alociranog niza
    ```

### 3.1 Niz objekata

Niz objekata može se koristiti na sličan način kao nizovi osnovnih tipova podataka. Evo primjera s nizom objekata klase `Osoba`:

```cpp
#include <iostream>
using namespace std;

class Osoba {
private:
    string ime;
    int godine;

public:
    // Konstruktor
    Osoba(string i, int g) : ime(i), godine(g) {}

    // Članske funkcije
    void predstaviSe() {
        cout << "Moje ime je " << ime << " i imam " << godine << " godina." << endl;
    }
};

int main() {
    // Deklaracija niza objekata klase Osoba
    Osoba nizOsoba[3] = {
        Osoba("Ana", 25),
        Osoba("Marko", 30),
        Osoba("Ivana", 28)
    };

    // Iteracija kroz niz i poziv metode za svaki objekt
    for (int i = 0; i < 3; i++) {
        nizOsoba[i].predstaviSe();
    }

    return 0;
}
```

U ovom primjeru, `nizOsoba` je niz objekata klase `Osoba`, a svaki objekt se inicijalizira pomoću odgovarajućeg konstruktora. Nakon toga, kroz niz se može iterirati i pozivati metode za svaki objekt. Ovo je korisno kad želite raditi s više instanci iste klase.

#### 3.1.1. Dinamički alocirani niza objekat

Primjer:

```cpp
#include <iostream>
using namespace std;

class Osoba {
private:
    string ime;
    int godine;

public:
    // Konstruktor
    Osoba(string i, int g) : ime(i), godine(g) {}

    // Članske funkcije
    void predstaviSe() {
        cout << "Moje ime je " << ime << " i imam " << godine << " godina." << endl;
    }
};

int main() {
    // Dinamička alokacija niza objekata klase Osoba
    Osoba *nizOsoba = new Osoba[3]{
        Osoba("Ana", 25),
        Osoba("Marko", 30),
        Osoba("Ivana", 28)
    };

    // Iteracija kroz dinamički alociran niz i poziv metode za svaki objekt
    for (int i = 0; i < 3; i++) {
        nizOsoba[i].predstaviSe();
    }

    // Dealokacija dinamički alociranog niza objekata
    delete[] nizOsoba;

    return 0;
}
```

U ovom primjeru, `new Osoba[3]` dinamički alocira niz objekata klase `Osoba` i inicijalizira ih odgovarajućim konstruktorom. Nakon upotrebe, niz se dealocira pomoću `delete[]`. Važno je koristiti `delete[]` kako biste ispravno dealocirali dinamički alociran niz objekata.

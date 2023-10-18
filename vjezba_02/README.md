# Vježba 2 - Preopterećene funkcije, klase i objekti, klasa string

## **1. Preopterećene funkcije**

- **Definicija:**
  - Preopterećene funkcije u C++-u omogućavaju definiranje više funkcija s istim imenom, ali različitim brojem ili tipovima parametara.
  
- **Primjer:**
  ```cpp
  void ispisi(int x);
  void ispisi(double x);
  ```
  - Funkcija `ispisi` je preopterećena za podršku cijelim i decimalnim brojevima.

---
## **2. Klase i objekti**

- **Definicija klase:**
  - Klasa je struktura koja definira svoje članove, uključujući atribute (varijable) i metode (funkcije). Klasa se može gledati kao špranca (obrazac) po kojoj se stvaraju objekti.

- **Definicija objekta:**
  - Objekt je instanca klase, stvoren iz definicije klase.

- **Primjer:**
  ```cpp
  class Osoba {
  public:
      string ime;
      int dob;
      void predstaviSe() {
          cout << "Ime: " << ime << ", Dob: " << dob << " godina." << endl;
      }
  };
  ```
  - Kreiranje objekta:
    ```cpp
    Osoba osoba1;
    osoba1.ime = "Ana";
    osoba1.dob = 25;
    osoba1.predstaviSe();
    ```

### 2.1 Privatne (private), zaštićene (protected) i javne (public) varijable

**Privatne varijable:** Ako član klase označimo kao privatni (`private`), onda je taj član dostupan samo unutar same klase. Objekti drugih instanci ne mogu direktno pristupiti privatnim članovima.

```cpp
class Osoba {
private:
    std::string ime;

public:
    void postaviIme(std::string novoIme) {
        ime = novoIme;
    }
};
```

**Zaštićene varijable:** Ako član klase označimo kao zaštićeni (`protected`), onda je taj član dostupan unutar same klase, ali i u klasama koje su izvedene iz nje. Ova vrsta pristupa je često korišćena u konceptu nasleđivanja.

```cpp
class Roditelj {
protected:
    int nekaVarijabla;
};

class Dijete : public Roditelj {
public:
    void postaviVrijednost(int novaVrijednost) {
        nekaVarijabla = novaVrijednost;
    }
};
```

**Javne varijable:** Ako član klase označimo kao javni (`public`), onda je taj član dostupan izvan klase. Objekti mogu direktno pristupiti javnim članovima.

```cpp
class Automobil {
public:
    std::string marka;
    int godinaProizvodnje;
};

Automobil auto1;
auto1.marka = "Toyota";
auto1.godinaProizvodnje = 2020;
```

Dobra praksa je često koristiti privatne varijable i napisati javne metode (getters i setters) za pristup i postavljanje vrijednosti tih varijabli. Ovo se naziva enkapsulacija i pomaže u održavanju i kontroli pristupa podacima unutar klase.

### 2.2 Konstruktori

Konstruktori su posebne metode u C++ koje se pozivaju prilikom kreiranja objekta klase. Njihova svrha je inicijalizacija objekta, postavljanje početnih vrijednosti članova klase ili izvođenje drugih inicijalizacijskih radnji.

Sintaksa konstruktora:

```cpp
class MojaKlasa {
public:
    // Konstruktor
    MojaKlasa() {
        // Inicijalizacija članova klase ili druge inicijalizacijske radnje
    }
};

// Kreiranje objekta i poziv konstruktora
MojaKlasa objekat;
```

Primjer s parametrima:

```cpp
class Osoba {
public:
    // Konstruktor s parametrima
    Osoba(std::string ime, int godine) {
        this->ime = ime;
        this->godine = godine;
    }

    void predstaviSe() {
        std::cout << "Moje ime je " << ime << " i imam " << godine << " godina." << std::endl;
    }

private:
    std::string ime;
    int godine;
};

// Kreiranje objekta i poziv konstruktora s parametrima
Osoba osoba1("John", 30);
osoba1.predstaviSe();  // Ispisuje "Moje ime je John i imam 30 godina."
```

Kao i metode (funkcije) konstruktori se mogu preopterećivati.

Primjer:

```cpp
#include <iostream>
#include <string>

class Osoba {
public:
    // Defaultni konstruktor
    Osoba() {
        ime = "Nepoznato";
        godine = 0;
    }

    // Konstruktor s jednim parametrom (ime)
    Osoba(std::string ime) {
        this->ime = ime;
        godine = 0;
    }

    // Konstruktor s dva parametra (ime i godine)
    Osoba(std::string ime, int godine) {
        this->ime = ime;
        this->godine = godine;
    }

    void predstaviSe() {
        std::cout << "Moje ime je " << ime << " i imam " << godine << " godina." << std::endl;
    }

private:
    std::string ime;
    int godine;
};

int main() {
    // Kreiranje objekata koristeći različite konstruktore
    // Poziva se defaultni konstruktor
    Osoba osoba1;     
    // Poziva se konstruktor s jednim parametrom               
    Osoba osoba2("John");    
    // Poziva se konstruktor s dva parametra        
    Osoba osoba3("Jane", 25);         
	// Ispisuje "Moje ime je Nepoznato i imam 0 godina."
    osoba1.predstaviSe();
    // Ispisuje "Moje ime je John i imam 0 godina."
    osoba2.predstaviSe();
    // Ispisuje "Moje ime je Jane i imam 25 godina."
    osoba3.predstaviSe();

    return 0;
}
```

### 2.3 Destruktori

Destruktori su metode koje se pozivaju kada objekt klase prestane postojati, tj. kada izađe iz opsega važećnosti ili kada se eksplicitno uništi. Destruktori su korisni za čišćenje resursa poput memorije ili zatvaranja otvorenih datoteka.

Sintaksa destruktora:

```cpp
class MojaKlasa {
public:
    // Destruktor
    ~MojaKlasa() {
        // Čišćenje resursa ili druge radnje pri uništavanju objekta
    }
};
```

Primjer:

```cpp
class Resurs {
public:
    Resurs() {
        std::cout << "Resurs je kreiran." << std::endl;
    }

    ~Resurs() {
        std::cout << "Resurs je uništen." << std::endl;
    }
};

int main() {
    Resurs resurs;  // Kreiranje objekta, poziva se konstruktor

    // Ostatak programa

    // Automatsko uništenje objekta kada izađe iz opsega važećnosti
    // Poziva se destruktor
    return 0;
}
```

U ovom primjeru, kada objekt `resurs` izađe iz opsega (na kraju `main` funkcije), automatski se poziva destruktor, što omogućava izvođenje potrebnih završnih radnji.

#### 2.3.1 Prednost destruktora?

Destruktori su korisni za izvođenje određenih radnji prije nego što objekt klase prestane postojati, kao što je oslobađanje resursa (poput memorije) ili obavljanje drugih operacija zatvaranja. Evo nekoliko razloga zašto su destruktori korisni:

- **Oslobađanje resursa:** Ako je objekt alocirao resurse tijekom svog životnog vijeka, destruktor omogućava oslobađanje tih resursa kada objekt više nije potreban. To može uključivati dealokaciju memorije, zatvaranje datoteka, prekidanje mrežnih veza i slično.

- **Automatsko izvršavanje:** Destruktori se automatski pozivaju kada objekt izlazi iz opsega važećnosti ili kada se eksplicitno uništi. Ovo automatsko ponašanje olakšava održavanje koda i sprječava curenje resursa.

**Garbage Collection u drugim jezicima:**
Iako C++ koristi destruktore za upravljanje resursima, jezici poput Java koriste mehanizam automatskog prikupljanja "smeća" (garbage collection) kako bi automatski oslobodili memoriju koju ne koristi nijedan objekt. Ovaj pristup olakšava upravljanje resursima i smanjuje potrebu za eksplicitnim destruktorima.

---
## **3. Klasa string**

- **Definicija:**
  - `string` je klasa koja predstavlja niz znakova u C++-u.

- **Operacije sa `string`-om:**
  - Manipulacija i rad s tekstualnim podacima, kao što su spajanje (`+`), pristup pojedinom znaku, duljina (`length()`).

- **Primjer:**
  ```cpp
  #include <iostream>
  #include <string>
  using namespace std;

  int main() {
      string ime = "Programiranje";
      cout << "Ime: " << ime << endl;
      cout << "Duljina stringa: " << ime.length() << endl;
      // Pristup znaku na određenom indeksu      
      char characterAtIndex = str[7]; // indeksiranje počinje od 0
      cout << "Znak na indeksu 7: " << characterAtIndex << endl;
      return 0;
  }
  ```

---

Ovi osnovni koncepti u C++-u, kao što su preopterećene funkcije, klase i objekti te klasa `string`, pružaju moćne alate za strukturiranje i organiziranje koda u objektno orijentiranom programiranju.

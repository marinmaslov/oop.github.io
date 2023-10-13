# Vježba 9 - STL i nasljeđivanje

## 1. Što je STL?

STL (Standard Template Library) je dio standardne C++ biblioteke koji pruža gotove implementacije čestih podatkovnih struktura i algoritama. Nudi efikasne i općenite alate za programere.

### 1.1 Kontejneri
Kontejneri su objekti koji služe za pohranu i manipulaciju skupovima podataka. Neki od klasičnih kontejnera u STL-u uključuju:

- **Vector**: Dinamički niz elemenata.
- **List**: Povezana lista elemenata.
- **Deque**: Dinamički niz elemenata s brzim dodavanjem i uklanjanjem s obje strane.
- **Queue**: Red (FIFO - First In, First Out).
- **Stack**: Stog (LIFO - Last In, First Out).
- **Map**: Asocijativni kontejner koji povezuje ključeve s vrijednostima.
- **Set**: Asocijativni kontejner koji sadrži jedinstvene elemente.

Prilikom rada s kontejnerima, važno je razumjeti performanse operacija poput dodavanja, brisanja i traženja kako biste odabrali odgovarajući kontejner za svoje potrebe.

### 1.2 Algoritmi

STL uključuje mnoge ugrađene algoritme koji se mogu primijeniti na kolekcije podataka. Neki od često korištenih algoritama uključuju:

- **sort()**: Sortira elemente kolekcije.
- **find()**: Pronalazi prvi element s određenom vrijednošću.
- **for_each()**: Primjenjuje funkciju na svaki element kolekcije.
- **count()**: Broji koliko puta se određena vrijednost pojavljuje u kolekciji.

Ovi algoritmi su vrlo moćni jer se mogu primijeniti na različite vrste kontejnera bez potrebe za pisanjem specifičnog koda za svaki kontejner.

### 1.3 Iteratori

Iteratori su objekti koji omogućuju prolazak kroz elemente kontejnera. STL uključuje različite vrste iteracija, uključujući:

- **begin()**: Vraća iterator koji pokazuje na prvi element.
- **end()**: Vraća iterator koji pokazuje iza posljednjeg elementa.

Korištenje iteracija omogućuje općenito pisanje koda, neovisno o vrsti kolekcije.

### 1.4 Funkcionalnosti u biblioteci `algorithm`

Biblioteka `algorithm` u STL-u pruža mnoge korisne funkcionalnosti. Neki od primjera uključuju:

- **accumulate()**: Zbraja elemente u rasponu.
- **max_element()**: Pronalazi najveći element u rasponu.
- **min_element()**: Pronalazi najmanji element u rasponu.

Ove funkcionalnosti često olakšavaju manipulaciju podacima i izbjegavaju potrebu za pisanjem specifičnih petlji.

### 1.5 Prednosti korištenja STL-a

- **Reusability (Ponovna upotreba)**: STL pruža gotove komponente koje možete koristiti u raznim situacijama, smanjujući potrebu za pisanjem potpuno novog koda.

- **Performance (Performanse)**: Implementacija STL-a često optimizira performanse, pružajući brze operacije koje su testirane i optimizirane.

- **Readability (Čitljivost)**: Kod koji koristi STL često je čišći i čitljiviji jer koristi visoko apstraktne koncepte.


### 1.6 Razmatranje

- **Memorijska Učinkovitost**: STL može koristiti dodatnu memoriju, posebno u dinamičkim strukturama poput vektora.

- **Prilagodba (Customization)**: Možete implementirati vlastite predloške i funkcije, ali to može biti složenije.

---

## 2 Što je nasljeđivanje?

### 2.1. Uvod u nasljeđivanje

Nasljeđivanje je ključna značajka objektno orijentiranog programiranja koja omogućava stvaranje novih klasa temeljenih na postojećim klasama. Klasa koja nasljeđuje zove se **izvedena klasa**, a klasa koja se nasljeđuje zove se **bazna klasa**. Izvedena klasa automatski nasljeđuje članove (varijable i funkcije) bazne klase.

### 2.2. Sintaksa nasljeđivanja

Sintaksa za deklariranje izvedene klase:

```cpp
class IzvedenaKlasa : public BaznaKlasa {
    // tijelo izvedene klase
};
```

- Ključna riječ `class` označava početak definicije klase.
- Ime izvedene klase (`IzvedenaKlasa`) slijedi nakon ključne riječi `class`.
- Operator `:` označava početak bloka nasljeđivanja.
- Ključna riječ `public` definira razinu pristupa nasljeđivanju (u ovom slučaju, javno nasljeđivanje).

### 2.3. Pristup članovima bazne klase u izvedenoj klasi

Članovi bazne klase mogu biti privatni, zaštićeni ili javni. Način pristupa ovim članovima u izvedenoj klasi ovisi o razini pristupa koju su imali u baznoj klasi:

- **Privatni članovi**: Naslijeđuju se, ali postaju privatni članovi izvedene klase.
- **Zaštićeni članovi**: Naslijeđuju se i postaju zaštićeni članovi izvedene klase.
- **Javni članovi**: Naslijeđuju se i ostaju javni članovi izvedene klase.

### 2.4. Konstruktori i destruktori u nasljeđivanju

Kada se stvara objekt izvedene klase, automatski se poziva konstruktor bazne klase, a nakon toga konstruktor izvedene klase. Slično, kad se uništava objekt izvedene klase, prvo se poziva destruktor izvedene klase, a zatim destruktor bazne klase.

### 2.5. Primjer nasljeđivanja

```cpp
#include <iostream>
using namespace std;

// Bazna klasa
class Osoba {
public:
    string ime;
    int dob;

    Osoba(string i, int d) : ime(i), dob(d) {}

    void predstaviSe() {
        cout << "Ime: " << ime << ", Dob: " << dob << " godina." << endl;
    }
};

// Izvedena klasa
class Student : public Osoba {
public:
    int brojIndeksa;

    Student(string i, int d, int br) : Osoba(i, d), brojIndeksa(br) {}

    void predstaviSe() {
        cout << "Student - Ime: " << ime << ", Dob: " << dob << " godina, Indeks: " << brojIndeksa << "." << endl;
    }
};

int main() {
    // Stvaranje objekta izvedene klase
    Student student1("Ana", 20, 12345);

    // Pozivanje metode iz bazne klase
    student1.predstaviSe();

    return 0;
}
```

U ovom primjeru, `Student` je izvedena klasa koja nasljeđuje klasu `Osoba`. Konstruktor izvedene klase poziva konstruktor bazne klase. Metoda `predstaviSe()` je preklopljena u izvedenoj klasi, a pristup članovima bazne klase (`ime` i `dob`) je automatski naslijeđen.

### 2.6. Pristup članovima bazne klase iz izvedene klase

```cpp
#include <iostream>
using namespace std;

// Bazna klasa
class Osoba {
protected:
    string ime;
    int dob;

public:
    Osoba(string i, int d) : ime(i), dob(d) {}

    void predstaviSe() {
        cout << "Ime: " << ime << ", Dob: " << dob << " godina." << endl;
    }
};

// Izvedena klasa
class Student : public Osoba {
public:
    int brojIndeksa;

    Student(string i, int d, int br) : Osoba(i, d), brojIndeksa(br) {}

    void predstaviSe() {
        cout << "Student - Ime: " << ime << ", Dob: " << dob << " godina, Indeks: " << brojIndeksa << "." << endl;
    }

    void predstaviRoditelja() {
        cout << "Roditelj - Ime: " << ime << ", Dob: " << dob << " godina." << endl;
    }
};

int main() {
    // Stvaranje objekta izvedene klase
    Student student1("Ana", 20, 12345);

    // Pozivanje metode iz bazne klase
    student1.predstaviSe();

    // Pristup članovima bazne klase iz izvedene klase
    student1.predstaviRoditelja();

    return 0;
}
```

U ovom primjeru, `ime` i `dob` su zaštićeni članovi bazne klase, što znači da ih izvedena klasa `Student` može koristiti direktno.

### 2.7 Zaštićene i privatne klase

Ako je klasa `Osoba` označena kao `private`, `Student` klasa je neće moći naslijediti. Nasljeđivanje s `private` pristupom značilo bi da su svi članovi klase `Osoba`, uključujući konstruktor i destruktor, privatni u klasi `Student`. To bi rezultiralo time da `Student` ne može pristupiti niti jednom članu klase `Osoba`.

Ako je klasa `Osoba` označena kao `protected`, `Student` će je moći naslijediti, ali privatni članovi klase `Osoba` ostat će joj nedostupni. Naslijeđivanje s `protected` pristupom omogućava izvedenoj klasi pristup zaštićenim i javnim članovima bazne klase, ali ne i privatnim članovima.

---

## 3. Rad s Listom stringova (z9.1)

### 3.1 Osnovni kod

U ovom zadatku, koristimo STL listu za pohranu stringova. Unosimo stringove s tipkovnice i ispisujemo ih.

```cpp
#include <iostream>
#include <list>
#include <string>
using namespace std;

int main() {
    string str;
    list<string> lst;
    list<string>::iterator iter;

    // Unos stringova dok se ne upiše "kraj"
    cin >> str;
    while (str != "kraj") {
        lst.push_back(str);
        cin >> str;
    }

    // Ispis stringova iz liste korištenjem iteratora
    for (iter = lst.begin(); iter != lst.end(); ++iter) {
        cout << *iter << endl;
    }

    return 0;
}
```

#### 3.2 Korištenje Iteratora

Koristimo iterator za prolazak kroz listu. Iterator je objekt koji omogućuje siguran pristup elementima kolekcije bez obzira na njezinu strukturu.

#### 3.3 Zašto ne koristimo uobičajenu for petlju sa indeksom?

Kod radimo s listom, a ne vektorom. Lista ne podržava pristup elemenata pomoću indeksa kao vektor. Iteratori su bolji izbor za prolazak kroz listu.

---

## 4. Uzlazno sortiranje vektora (z9.2)

### 4.1 Dodavanje brojeva u Vektor

Ovdje koristimo vektor za pohranu cijelih brojeva. Unosimo brojeve dok ne upišemo 0, a zatim ih ispisujemo.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    int a;
    vector<int> v;
    vector<int>::iterator iter;

    // Unos brojeva dok se ne upiše 0
    cin >> a;
    while (a != 0) {
        v.push_back(a);
        cin >> a;
    }

    // Ispis brojeva iz vektora
    for (iter = v.begin(); iter != v.end(); ++iter) {
        cout << *iter << endl;
    }

    return 0;
}
```

### 4.2 Korištenje STL funkcije `sort()`

Koristimo funkciju `sort()` za uzlazno sortiranje elemenata u vektoru. Ova funkcija dolazi iz STL biblioteke.

```cpp
// Sortiranje vektora uzlazno
sort(v.begin(), v.end());
```

---

## 5. Različite klase za različite medije (z9.3)

### 5.1 Klase LP, CD, DVD

Definiramo tri klase (`LP`, `CD`, `DVD`) koje predstavljaju različite medije. Svaka klasa ima nasljeđivanje od temeljne klase `ploca`.

```cpp
class LP // stari vinil
{
public:
    string naslov;
    string izvodjac;
    int trajanje;  // u minutama
    int RPM;       // broj okretaja

    LP() {
        naslov = "";
        izvodjac = "";
        trajanje = 45;
        RPM = 45;
    }
};

class CD // compact disc
{
public:
    string naslov;
    string izvodjac;
    int trajanje;  // u minutama
    bool RW;       // je li RW

    CD() {
        naslov = "";
        izvodjac = "";
        trajanje = 45;
        RW = true;
    }
};

class DVD // digital video disc
{
public:
    string naslov;
    string izvodjac;
    int

 trajanje;  // u minutama
    bool dvostrani;  // je li dvostrani

    DVD() {
        naslov = "";
        izvodjac = "";
        trajanje = 45;
        dvostrani = true;
    }
};
```

### 5.2 Nasljeđivanje i konstruktori

Koristimo nasljeđivanje da bismo izbjegli dupliciranje koda i pojednostavili strukturu koda. Također, koristimo konstruktore za inicijalizaciju članova.

```cpp
class ploca // izvorna klasa
{
public:
    string naslov;
    string izvodjac;
    int trajanje;

    ploca() {
        naslov = "";
        izvodjac = "";
        trajanje = 45;
    }
};

class LP : public ploca
{
public:
    int RPM;

    LP() : ploca() {
        RPM = 45;
    }
};

class CD : public ploca
{
public:
    bool RW;

    CD() : ploca() {
        RW = true;
    }
};

class DVD : public ploca
{
public:
    bool dvostrani;

    DVD() : ploca() {
        dvostrani = true;
    }
};
```

### 5.3 Prednosti nasljeđivanja

Nasljeđivanje omogućuje ponovno korištenje koda, smanjuje redundanciju i čini strukturu programa modularnom. Svaka klasa može imati svoje specifičnosti, a općeniti atributi se nasljeđuju.

---

## 6. Klasa Tocka2D (z9.4)

### 6.1 Osnovne metode klase Tocka2D

Definiramo klasu `Tocka2D` koja predstavlja točku u dvodimenzionalnom prostoru. Ključne metode su `SetX`, `SetY`, `GetX`, i `GetY` za postavljanje i dohvaćanje koordinata.

```cpp
class Tocka2D {
public:
    Tocka2D();
    void SetX(double x);
    void SetY(double y);
    double GetX();
    double GetY();

protected:
    double m_x, m_y;
};

Tocka2D::Tocka2D() {
    m_x = 0.0;
    m_y = 0.0;
}

void Tocka2D::SetX(double x) {
    m_x = x;
}

void Tocka2D::SetY(double y) {
    m_y = y;
}

double Tocka2D::GetX() {
    return m_x;
}

double Tocka2D::GetY() {
    return m_y;
}
```

### 6.2 Inicijalizacija članova klase

Konstruktor `Tocka2D` postavlja početne vrijednosti koordinata. Metode `SetX`, `SetY`, `GetX`, i `GetY` omogućuju manipulaciju tim koordinatama.

---

### 7. Korištenje Iteratora za unos vektora (z9.6)

### 7.1 Promjena `for` petlje s indeksom u `for` petlju s iteratorom

Kada radimo s vektorom, korisno je koristiti iterator za prolazak kroz elemente umjesto uobičajene for petlje sa indeksom. To povećava fleksibilnost i čini kôd čitljivijim.

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<double> vec;
    double val;

    cout << "Unos proizvoljnog niza brojeva u vektor." << endl;
    cout << "Unos završava kada se otkuca neko slovo!" << endl;

    // Punjenje vektora
    while (cin >> val) {
        vec.push_back(val);
    }

    // Računanje sume i srednje vrijednosti
    double sum = 0;
    for (auto it = vec.begin(); it != vec.end(); ++it) {
        sum += *it;
    }

    double avg = sum / vec.size();

    cout << "Suma od " << vec.size() << " elemenata: " << sum << ". Srednja vrijednost: " << avg << endl;

    return 0;
}
```

---

## 8. Zaposlenik i nasljeđivanje

### 8.1 Definiranje Temeljne Klase `Zaposlenik` (z9.7)

Definiramo temeljnu klasu `Zaposlenik` koja bilježi zajedničke informacije za sve zaposlenike, poput imena, prezimena, fakulteta, emaila i jezika.

```cpp
#include <iostream>
#include <string>
using namespace std;

class Zaposlenik {
public:
    string ime;
    string prezime;
    string fakultet;
    string email;

    void SetIme(string i) { ime = i; }
    void SetPrezime(string p) { prezime = p; }
    void SetFakultet(string f) { fakultet = f; }
    void SetEmail(string e) { email = e; }
};
```

### 8.2 Izvedene klase: `Programer`, `Dizajner`, `Tester`

Izvedene klase nasljeđuju od temeljne klase i dodaju specifične informacije za svaki tip zaposlenika.

```cpp
class Programer : public Zaposlenik {
public:
    string programskiJezik;
};

class Dizajner : public Zaposlenik {
public:
    string grafickiAlati;
};

class Tester : public Zaposlenik {
public:
    string vrsteTestiranja;
};
```

### 8.3 Upotreba nasljeđivanja i primjer

Nasljeđivanje omogućuje različitim klasama dijeljenje zajedničkih svojstava i metoda, čime se smanjuje dupliciranje koda. Primjer upotrebe:

```cpp
int main() {
    Programer p;
    p.SetIme("John");
    p.SetPrezime("Doe");
    p.SetFakultet("FER");
    p.SetEmail("john.doe@example.com");
    p.programskiJezik = "C++";

    cout << "Programer: " << p.ime << " " << p.prezime << endl;
    cout << "Fakultet: " << p.fakultet << endl;
    cout << "Email: " << p.email << endl;
    cout << "Programski jezik: " << p.programskiJezik << endl;

    return 0;
}
```

Ovaj primjer prikazuje kako izvedena klasa `Programer` koristi svoje specifične atribute, ali i nasljeđuje zajedničke atribute i metode od temeljne klase `Zaposlenik`.

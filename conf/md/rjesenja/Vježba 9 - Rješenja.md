## **Zadatak 9.1**

### Korak 1:
Program čita stringove sa tipkovnice sve dok ne upišete "kraj" i sprema ih u listu. Nakon toga ispisuje stringove iz liste.

```cpp
#include <iostream>
#include <list>
#include <string>
using namespace std;

int main() {
    string str;
    list<string> lst;
    list<string>::iterator iter;

    // čita stringove sa tipkovnice, dok se ne upiše "kraj" i upisuje ih u listu
    cin >> str;
    while (str != "kraj") {
        lst.push_back(str);
        cin >> str;
    }

    cout << endl;

    // ispisuje stringove iz liste pomoću for petlje sa iteratorom
    for (iter = lst.begin(); iter != lst.end(); ++iter) {
        cout << *iter << endl;
    }

    return 0;
}
```

Ovaj program čita stringove sa tipkovnice dok se ne unese "kraj" i sprema ih u listu. Zatim ispisuje sve stringove iz liste.

**Zašto se ne koristi uobičajena for petlja s indeksom?**
Liste u C++ nemaju pristup po indeksu kao nizovi. Elementima liste pristupa se pomoću iteratora. Iteratori su pokazivači koji pokazuju na element, omogućujući iteraciju kroz elemente.

### Korak 2:
Dodajte kod za obrtanje redoslijeda liste.

```cpp
// Obrtanje redoslijeda liste koristeći funkciju reverse()
lst.reverse();
```

### Korak 3:
Dodajte kod za spremanje stringova iz liste u datoteku "lista.txt".

```cpp
#include <fstream>

// Snimanje stringova iz liste u datoteku
ofstream file("lista.txt");
for (iter = lst.begin(); iter != lst.end(); ++iter) {
    file << *iter << endl;
}
file.close();
```

---

## **Zadatak 9.2**

### Korak 1:
Dodajte kod za uzlazno sortiranje brojeva u vektoru.

```cpp
#include <algorithm>

// Uzlazno sortiranje brojeva u vektoru
sort(v.begin(), v.end());
```

---

## **Zadatak 9.3**

### Korak 1:
Broj linija koda za definiciju klasa LP, CD i DVD:

```plaintext
LP: 19 linija
CD: 18 linija
DVD: 18 linija
```

### Korak 2:
Izmijenite kod u z932.cpp. Klase LP, CD i DVD nasljeđuju klasu ploca.

```cpp
class LP : public ploca
{
public:
    int RPM;
    LP() : ploca(), RPM(45) {}
};

class CD : public ploca
{
public:
    bool RW;
    CD() : ploca(), RW(true) {}
};

class DVD : public ploca
{
public:
    bool dvostrani;
    DVD() : ploca(), dvostrani(true) {}
}
```

Za definiciju klasa `LP`, `CD`, i `DVD` s nasljeđivanjem od osnovne klase `ploca`, potrebno je ukupno 15 linija koda (3 linije po članu klase).

### Korak 3:
Dodajte klasu MP3CD.

```cpp
class MP3CD : public ploca
{
public:
    string izvor;
    MP3CD() : ploca(), izvor("vinil") {}
};
```

---

## **Zadatak 9.4**

### Korak 1:
Opišite klasu Tocka2D.

```cpp
class Tocka2D {
public:
    Tocka2D();  // Konstruktor
    void SetX(double x);
    void SetY(double y);
    double GetX();
    double GetY();

protected:
    double m_x, m_y;  // Koordinate točke
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

Klasa `Tocka2D` predstavlja točku u dvodimenzionalnom prostoru. Klasi su dodane privatne varijable `m_x` i `m_y` koje predstavljaju koordinate točke. Osim toga, klasa sadrži konstruktor za postavljanje početnih vrijednosti koordinata, te metode za postavljanje (`SetX`, `SetY`) i dohvaćanje (`GetX`, `GetY`) koordinata.

### Korak 2:
Definirajte klasu Tocka3D koristeći nasljeđivanje.

```cpp
class Tocka3D : public Tocka2D {
public:
    Tocka3D();  // Konstruktor
    void SetZ(double z);
    double GetZ();
    bool operator==(const Tocka3D& other);  // Operator usporedbe

protected:
    double m_z;  // Koordinata Z u trodimenzionalnom prostoru
};

Tocka3D::Tocka3D() : Tocka2D() {
    m_z = 0.0;
}

void Tocka3D::SetZ(double z) {
    m_z = z;
}

double Tocka3D::GetZ() {
    return m_z;
}

bool Tocka3D::operator==(const Tocka3D& other) {
    return (m_x == other.m_x) && (m_y == other.m_y) && (m_z == other.m_z);
}
```

---

# Dodatni zadaci

## **Zadatak 9.5**

Promijenite kod z831.cpp.

```cpp
#include <iostream>
#include "tvector.h"

using namespace std;

int main() {
    tvector<double> vec;
    double val;

    cout << "Unos proizvoljnog niza brojeva u vektor." << endl;
    cout << "Unos zavrsava kada se otkuca neko slovo!" << endl;

    while (cin >> val) {
        vec.push_back(val);
    }

    double sum = 0;
    for (auto it = vec.begin(); it != vec.end(); ++it) {
        sum += *it;
    }
    
    double avg = sum / vec.size();

    cout << "Suma od " << vec.size() << " elemenata: " << sum
         << ". Srednja vrijednost: " << avg << endl;

    return 0;
}
```

---

## **Zadatak 9.6**

**Zadatak 9.6:**

Dopunjeni kod za pretragu članova u vektoru koristeći funkciju `find`:
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    vector<int> v = {1, 2, 3, 4, 5};

    // Vrijednost koju želimo pretražiti
    int targetValue = 3;

    auto it = find(v.begin(), v.end(), targetValue);

    if (it != v.end()) {
        cout << "Vrijednost pronađena na poziciji: " << distance(v.begin(), it) << endl;
    } else {
        cout << "Vrijednost nije pronađena." << endl;
    }

    return 0;
}
```

---

## **Zadatak 9.7**

Definicija temeljne klase Zaposlenik i izvedenih klasa Programer, Dizajner, Tester:
```cpp
#include <iostream>
#include <string>

using namespace std;

class Zaposlenik {
public:
    string imePrezime;
    string email;

    Zaposlenik() {
        imePrezime = "";
        email = "";
    }

    // Dodajte dodatne metode prema potrebi
};

class Programer : public Zaposlenik {
public:
    string jezici;

    Programer() {
        jezici = "";
    }

    // Dodajte dodatne metode prema potrebi
};

class Dizajner : public Zaposlenik {
public:
    string alati;
    string fakultet;

    Dizajner() {
        alati = "";
        fakultet = "";
    }

    // Dodajte dodatne metode prema potrebi
};

class Tester : public Zaposlenik {
public:
    string vrsteTestiranja;

    Tester() {
        vrsteTestiranja = "";
    }

    // Dodajte dodatne metode prema potrebi
};

int main() {
    // Primjer korištenja klasa
    Programer p;
    p.imePrezime = "John Doe";
    p.email = "john.doe@example.com";
    p.jezici = "C++, Java";

    cout << "Programer: " << p.imePrezime << ", Email: " << p.email << ", Jezici: " << p.jezici << endl;

    return 0;
}
```

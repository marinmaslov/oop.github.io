# Vježba 10 - Polimorfizam i virtualne metode

## 1. Uvod

Polimorfizam je ključni koncept u objektno orijentiranom programiranju (OOP) koji omogućuje jednom sučelju (interface) da ima različite implementacije. To se postiže korištenjem virtualnih metoda i apstraktnih klasa.

## 2. Apstraktne klase

Apstraktne klase su klase koje imaju barem jednu čisto virtualnu funkciju. Čisto virtualna funkcija označava da nema implementacije u baznoj klasi i mora se implementirati u izvedenim klasama. Apstraktne klase se koriste kao sučelje koje definira metode, ali ostavlja implementaciju za druge klase.

```cpp
#include <iostream>
#include <string>
using namespace std;

// Apstraktna klasa
class Oblik {
public:
    virtual void iscrtaj() const = 0; // Čisto virtualna funkcija
};

// Izvedene klase
class Krug : public Oblik {
public:
    void iscrtaj() const override {
        cout << "Crtam krug." << endl;
    }
};

class Pravokutnik : public Oblik {
public:
    void iscrtaj() const override {
        cout << "Crtam pravokutnik." << endl;
    }
};
```

## 3. Virtualne metode

Virtualne metode omogućuju izvedenim klasama da prenesu svoje verzije funkcija iz bazne klase. To je ključno za postizanje polimorfizma.

```cpp
#include <iostream>
#include <string>
using namespace std;

// Bazna klasa
class Vozilo {
public:
    virtual void vozi() const {
        cout << "Vozilo vozi." << endl;
    }
};

// Izvedene klase
class Auto : public Vozilo {
public:
    void vozi() const override {
        cout << "Auto vozi." << endl;
    }
};

class Bicikl : public Vozilo {
public:
    void vozi() const override {
        cout << "Bicikl vozi." << endl;
    }
};

int main() {
    Auto auto1;
    Bicikl bicikl1;

    Vozilo* vozila[] = {&auto1, &bicikl1};

    for (const auto* vozilo : vozila) {
        vozilo->vozi(); // Polimorfizam
    }

    return 0;
}
```

## 4. Korištenje polimorfizma

Polimorfizam omogućuje jednostavno korištenje različitih implementacija bazne klase, bez obzira na stvarnu tipizaciju objekta.

```cpp
#include <iostream>
#include <string>
using namespace std;

class Osoba {
public:
    virtual void predstaviSe() const {
        cout << "Ja sam osoba." << endl;
    }
};

class Student : public Osoba {
public:
    void predstaviSe() const override {
        cout << "Ja sam student." << endl;
    }
};

class Profesor : public Osoba {
public:
    void predstaviSe() const override {
        cout << "Ja sam profesor." << endl;
    }
};

int main() {
    Osoba* osobe[] = {new Student, new Profesor};

    for (const auto* osoba : osobe) {
        osoba->predstaviSe(); // Polimorfizam
    }

    for (const auto* osoba : osobe) {
        delete osoba; // Oslobađanje memorije
    }

    return 0;
}
```

## 5. Zaključak

Polimorfizam omogućuje fleksibilnost u korištenju klasa, čime se olakšava održavanje koda i povećava njegova čitljivost. Korištenje apstraktnih klasa i virtualnih metoda ključno je za postizanje ovog koncepta.

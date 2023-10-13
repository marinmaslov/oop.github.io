# Vježba 6 - Preopterećenje operatora, petlje i rekurzija

## 1. Preopterećenje operatora

Svaka klasa u C++ implicitno dolazi s nekim operatorima. Na primjer, dodavanje (`+`), oduzimanje (`-`), množenje (`*`), dijeljenje (`/`), i mnogi drugi operatori rade s ugrađenim tipovima podataka. No, kad radimo s vlastitim tipovima podataka (klasama), možemo definirati kako će se ti operatori ponašati pomoću **preopterećenja operatora**.

Evo osnovne sintakse za preopterećivanje operatora:

```cpp
tip_podataka operator operator_simbol (parametri) {
    // implementacija
}
```

Ovdje, `tip_podataka` označava tip podataka koji će operator vratiti, `operator_simbol` je simbol operatora koji preopterećujemo (npr., `+`, `-`, `*`, `/`), a `parametri` su parametri koje operator prima.

Primjer preopterećenja operatora za zbrajanje kompleksnih brojeva:

```cpp
#include <iostream>

class Complex {
private:
    double real;
    double imag;

public:
    Complex() : real(0.0), imag(0.0) {}

    Complex operator+(const Complex& other) {
        Complex sum;
        sum.real = this->real + other.real;
        sum.imag = this->imag + other.imag;
        return sum;
    }
};

int main() {
    Complex a(3.0, 4.0);
    Complex b(1.5, 2.5);

    Complex sum = a + b;  // Ovdje se poziva preopterećeni operator za zbrajanje.

    return 0;
}
```

U ovom primjeru, `operator+` je preopterećen za klasu `Complex`. Kada napišete `a + b`, poziva se `operator+` definiran unutar klase `Complex`. Bitno je napomenuti da `operator+` može biti preopterećen kao član klase (`Complex operator+(const Complex& other)`) ili kao prijateljska funkcija izvan klase.

Preopterećenje operatora vam omogućava prilagodbu ponašanja operatora prema vašim potrebama i poboljšava čitljivost vašeg koda.

Proširenje primjera s preopterećenjem operatora za ispis (`<<`) kompleksnih brojeva:

```cpp
#include <iostream>

class Complex {
private:
    double real;
    double imag;

public:
    Complex() : real(0.0), imag(0.0) {}

    Complex operator+(const Complex& other) {
        Complex sum;
        sum.real = this->real + other.real;
        sum.imag = this->imag + other.imag;
        return sum;
    }

    // Dodajte i operator za ispis (<<) kako biste mogli lakše ispisivati kompleksne brojeve.
    friend std::ostream& operator<<(std::ostream& os, const Complex& c);
};

std::ostream& operator<<(std::ostream& os, const Complex& c) {
    os << c.real << " + i * " << c.imag;
    return os;
}

int main() {
    Complex a(3.0, 4.0);
    Complex b(1.5, 2.5);

    Complex sum = a + b;

    std::cout << "a = " << a << std::endl;
    std::cout << "b = " << b << std::endl;
    std::cout << "a + b = " << sum << std::endl;

    return 0;
}
```

Ovaj program preopterećuje operator `+` za zbrajanje kompleksnih brojeva. Također, koristi prijateljski operator `<<` kako bi olakšao ispis kompleksnih brojeva.

---

## 2. Petlje

**Petlje** su konstrukti koji omogućavaju izvođenje istog bloka koda više puta. 

U C++-u postoje tri osnovne vrste petlji: `for`, `while` i `do-while`. Svaka od njih ima svoje specifičnosti i koristi se u različitim situacijama.

### 2.1 `for` petlja

`for` petlja se koristi kada unaprijed znamo koliko puta želimo ponoviti blok koda. Sintaksa `for` petlje je:

```cpp
for (inicijalizacija; uvjet; ažuriranje/korak iteracije) {
    // Tijelo petlje
}
```

Primjer:

```cpp
#include <iostream>

int main() {
    for (int i = 0; i < 5; i++) {
        std::cout << i << " ";
    }

    return 0;
}
```

Ova petlja će ispisati brojeve od 0 do 4. Varijabla `i` se inicijalizira na 0, petlja se izvršava dok je `i < 5`, i nakon svake iteracije, `i` se povećava za 1 (`i++`).

### 2.2 `while` petlja

`while` petlja se koristi kada želimo ponavljati blok koda dok je određeni uvjet ispunjen. Sintaksa `while` petlje je:

```cpp
while (uvjet) {
    // Tijelo petlje
}
```

Primjer:

```cpp
#include <iostream>

int main() {
    int i = 0;
    while (i < 5) {
        std::cout << i << " ";
        i++;
    }

    return 0;
}
```

Ova petlja radi na isti način kao i prethodna `for` petlja, ispisujući brojeve od 0 do 4.

### 2.3 `do-while` petlja:

`do-while` petlja je slična `while` petlji, ali uvjet se provjerava nakon izvršenja bloka koda, što znači da će se tijelo petlje izvršiti barem jednom. Sintaksa `do-while` petlje je:

```cpp
do {
    // Tijelo petlje
} while (uvjet);
```

Primjer:

```cpp
#include <iostream>

int main() {
    int i = 0;
    do {
        std::cout << i << " ";
        i++;
    } while (i < 5);

    return 0;
}
```

Ova petlja također ispisuje brojeve od 0 do 4, ali garantira da će se tijelo petlje izvršiti barem jednom.

Ovisno o situaciji, odabirete odgovarajuću petlju prema uvjetima problema koji rješavate.

---

### 3. Rekurzija

**Rekurzija** je tehnika gdje funkcija poziva samu sebe.

Evo primjera rekurzivne funkcije koja izračunava faktorijel broja:

```cpp
#include <iostream>

// Rekurzivna funkcija za izračun faktorijela
unsigned long long factorial(int n) {
    if (n == 0 || n == 1) {
        return 1;
    } else {
        return n * factorial(n - 1);
    }
}

int main() {
    int n = 5;
    std::cout << "Faktorijel od " << n << " je: " << factorial(n) << std::endl;

    return 0;
}
```

Ovo je tipičan primjer rekurzivne funkcije. Sada ćemo prikazati kako bismo to mogli implementirati pomoću `for` petlje. Ovdje koristimo `for` petlju da iteriramo kroz brojeve od 1 do n i množimo ih zajedno.

```cpp
#include <iostream>

// Funkcija za izračun faktorijela pomoću for petlje
unsigned long long factorial(int n) {
    unsigned long long result = 1;
    for (int i = 1; i <= n; ++i) {
        result *= i;
    }
    return result;
}

int main() {
    int n = 5;
    std::cout << "Faktorijel od " << n << " je: " << factorial(n) << std::endl;

    return 0;
}
```

Ova verzija koristi `for` petlju umjesto rekurzije. Bitno je napomenuti da nije uvijek moguće jednostavno zamijeniti rekurziju `for` petljom, a rekurzija se često koristi kada je prirodna struktura problema takva da se može elegantno izraziti rekurzivnom funkcijom.

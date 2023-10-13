## **Zadatak 6.1**

### Korak 1:
Nakon što se pokrene program, ispis će biti sljedeći:

```
a = 6.6 + i * 4.7
b = 2.6 + i * 3.4
c = a + b
c = 9.2 + i * 8.1
```

Ovaj program definira klasu `kompleks` koja predstavlja kompleksni broj s realnim i imaginarnim dijelom. U `main` funkciji stvaraju se dva kompleksna broja `a` i `b`, zatim se njihov zbroj pohranjuje u kompleksni broj `c`, te se ispisuju originalni brojevi i rezultat zbroja.

### Korak 2:
Dodajmo preopterećeni operator za oduzimanje u klasi `kompleks`:

```cpp
kompleks kompleks::operator - (const kompleks& d) {
    kompleks razlika(real - d.real, imag - d.imag);
    return razlika;
}
```

U `main` funkciji nakon zbrajanja dodajmo i oduzimanje:

```cpp
// oduzimanje dva kompleksna broja - poziva preopterećeni operator klase kompleks
kompleks d = a - b;
// ispis razlike
cout << "d = a - b" << endl;
cout << "d = " << d.getReal() << " + i * " << d.getImag() << endl;
```

### Korak 3:
Implementirajmo i preopterećeni operator +=:

```cpp
kompleks& kompleks::operator += (const kompleks& d) {
    real += d.real;
    imag += d.imag;
    return *this;
}
```

U `main` funkciji, nakon zbrajanja i oduzimanja, dodajmo i povećanje `c` za vrijednost `a`:

```cpp
// povećanje kompleksnog broja c za vrijednost kompleksnog broja a
c += a;
cout << "c += a" << endl;
cout << "c = " << c.getReal() << " + i * " << c.getImag() << endl;
```

---

## **Zadatak 6.2**

### Korak 1:
Napišimo preopterećene operatore za usporedbu (`<`, `>`) u klasi `kompleks`:

```cpp
bool operator > (const kompleks& c1, const kompleks& c2) {
    return (pow(c1.real, 2) + pow(c1.imag, 2)) > (pow(c2.real, 2) + pow(c2.imag, 2));
}
```

### Korak 2:
U `main` funkciji, umjesto korištenja operatora `<`, koristimo operator `>`:

```cpp
// za usporedbu a i b koristimo operator usporedbe koji smo dodali klasi
if (a > b)
    cout << "a je veće od b!" << endl;
else
    cout << "a je manje ili jednako b!" << endl;
```

### Korak 3:
Dodajmo preopterećeni operator `+=` u klasi `kompleks`:

```cpp
kompleks& kompleks::operator += (const kompleks& d) {
    real += d.real;
    imag += d.imag;
    return *this;
}
```

U `main` funkciji, na kraju programa, povećajmo vrijednost `c` za vrijednost `a` koristeći operator `+=`:

```cpp
// povećanje kompleksnog broja c za vrijednost kompleksnog broja a
c += a;
cout << "c += a" << endl;
cout << "c = " << c.getReal() << " + i * " << c.getImag() << endl;
```

---

## **Zadatak 6.3**

### Korak 1:
Implementirajmo operatore pridjele (`operator=`) i indeksnog operatora (`operator[]`) u klasi `iarray`:

```cpp
iarray& iarray::operator=(const iarray& rhs) {
    if (this != &rhs) {
        delete[] m_arr;
        init(rhs.m_arr, rhs.m_size);
    }
    return *this;
}

int& iarray::operator[](int index) {
    // Dodajte provjeru da li je indeks unutar granica niza
    if (index < 0 || index >= m_size) {
        // Handle the error, throw an exception, or return a default value
        cerr << "Index out of bounds!" << endl;
        exit(1);
    }
    return m_arr[index];
}
```

### Korak 2:
U `main` funkciji testirajmo operatore pridjele i indeksnog operatora:

```cpp
iarray arr1(5);
arr1[0] = 1;
arr1[1] = 2;
arr1[2] = 3;
arr1[3] = 4;
arr1[4] = 5;

iarray arr2 = arr1;  // operator pridjele
arr2[0] = 10;        // promjena vrijednosti na indeksu 0

cout << "arr1: ";
for (int i = 0; i < arr1.size(); i++) {
    cout << arr1[i] << " ";
}
cout << endl;

cout << "arr2: ";
for (int i = 0; i < arr2.size(); i++) {
    cout << arr2[i] << " ";
}
cout << endl;
```

---

# Dodatni zadaci

## **Zadatak 6.4**

### Korak 1:
Za Zadatak 6.4, korak 1, imamo program koji računa potenciju broja. Evo opisa tijeka izvođenja programa:

1. **Unos Baze i Potencije:**
   - Program započinje tražeći unos baze od korisnika, koju korisnik upisuje s tastature.
   - Zatim program traži unos potencije od korisnika.

2. **Inicijalizacija Varijabli:**
   - Varijable `i`, `p`, `b`, i `r` se deklariraju.
   - `r` se postavlja na 1, jer je to inicijalna vrijednost rezultata.

3. **Petlja za Potenciranje:**
   - Koristi se `for` petlja za potenciranje baze.
   - Petlja prolazi kroz `p` iteracija, povećavajući `r` množenjem s bazom `b` u svakom koraku.

4. **Ispis Rezultata:**
   - Nakon završetka petlje, program ispisuje rezultat potenciranja.

Primjer izvođenja programa s unosom baze 2 i potencije 10:
```plaintext
Upisite bazu: 2
Upisite potenciju: 10
2 na 10 je: 1024
```

U ovom primjeru, program izračunava 2^10, što je 1024, i ispisuje rezultat.

### Korak 2:
Promijenimo for petlju u while petlju:

```cpp
// while petlja umjesto for petlje
while (i < p) {
    r = r * b;
    i++;
}
```

### Korak 3:
Koristimo rekurzivnu funkciju umjesto petlje:

```cpp
// rekurzivna funkcija za računanje potencije
unsigned int power(unsigned int base, unsigned int exponent) {
    if (exponent == 0)
        return 1;
    else
        return base * power(base, exponent - 1);
}

// poziv rekurzivne funkcije umjesto petlje
r = power(b, p);
```

---

# Dodatni zadaci

## Zadatak 6.5:

Dodajemo podršku za negativne potencije u rekurzivnoj funkciji:

```cpp
// rekurzivna funkcija za računanje potencije (s podrškom za negativne potencije)
double power(double base, int exponent) {
    if (exponent == 0)
        return 1;
    else if (exponent > 0)
        return base * power(base, exponent - 1);
    else
        return 1.0 / (base * power(base, -exponent - 1));
}
```

U `main` funkciji testiramo:

```cpp
// Testiranje rekurzivne funkcije s negativnom potencijom
double result = power(2, -3);
cout << "2^-3 = " << result << endl;
```

Ovaj kod će ispisati `2^-3 = 0.125`, što je ispravan rezultat.
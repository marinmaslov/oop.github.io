## **Zadatak 7.1:*

### Korak 1:
* Program koristi `ofstream` za otvaranje datoteke "cities" i zapisuje nekoliko gradova u tu datoteku.

Sadržaj datoteke "cities" nakon pokretanja programa:
```
Atlanta Baltimore Cincinnati Dallas zzz zzz
```

### Korak 2:
* Učitava sadržaj datoteke "cities" koristeći `ifstream` i ispisuje ga na konzolu.

Ispis programa:
```
Atlanta Baltimore Cincinnati Dallas zzz zzz
```

### Korak 3:
* Program se modificira tako da otvara dodatnu datoteku "filter" te u nju zapisuje gradove koji nisu "zzz". Nakon toga, zatvaraju se obje datoteke, a sadržaj "filter" datoteke ispisuje na ekran.

```cpp
#include <iostream>
#include <fstream>
#include <string>

using namespace std;

int main(void)
{
    ifstream in_file("cities");

    if (!in_file)
    {
        cerr << "Neuspjesno otvaranje datoteke." << endl;
        return 1;
    }

    ofstream out_file_filter("filter");

    if (!out_file_filter)
    {
        cerr << "Neuspjesno otvaranje datoteke filter za pisanje." << endl;
        return 1;
    }

    string string_A;

    while (in_file >> string_A)
    {
        cout << string_A << " ";

        if (string_A != "zzz")
        {
            out_file_filter << string_A << " ";
        }
    }

    in_file.close();
    out_file_filter.close();

    // Ispis sadržaja datoteke filter
    ifstream filter_file("filter");

    if (!filter_file)
    {
        cerr << "Neuspjesno otvaranje datoteke filter za citanje." << endl;
        return 1;
    }

    cout << "\nSadrzaj datoteke filter: ";
    while (filter_file >> string_A)
    {
        cout << string_A << " ";
    }

    filter_file.close();

    return 0;
}
```

Ovdje smo dodali otvaranje i pisanje u datoteku "filter" unutar petlje te ispisivanje njenog sadržaja na kraju programa.

Ispis programa:
```
Atlanta Baltimore Cincinnati Dallas
```

**Zaključak:** Program filtrira gradove i sprema samo one koji nisu "zzz" u drugu datoteku "filter".

---

## **Zadatak 7.2**

### Korak 1:
* Program prima dva kompleksna broja od korisnika i uspoređuje ih operatorom `<`. Ispisuje rezultat na konzolu.

Ispis programa (primjer unosa: a = 2 + i * 3, b = 1 + i * 4):
```
Upisite dva kompleksna broja (dva para vrijednosti):
2 3
1 4
Upisali ste brojeve
a = 2 + i * 3
b = 1 + i * 4
a je vece ili jednako b!
```

### Korak 2:
* Dodaje se preopterećeni operator `<<` za ispis kompleksnih brojeva na konzolu. Izmjenjuje se ispis u funkciji `main` koristeći ovaj operator.

```cpp
ostream& operator << (ostream &s, kompleks &c1) {
    s << setprecision(13) << c1.getReal() << " + i * " << c1.getImag();
    return s;
}
```

```cpp
int main() {
    kompleks a;
    kompleks b;
    
    cout << "Upisite dva kompleksna broja (dva para vrijednosti):" << endl;
    cin >> a;
    cin >> b;
    
    cout << "Upisali ste brojeve" << endl;
    cout << " a = " << a << endl;
    cout << " b = " << b << endl;
    
    if (a < b)
        cout << "a je manje od b!" << endl;
    else
        cout << "a je vece ili jednako b!" << endl;

    return 0;
}
```

Ispis programa:
```
Upisite dva kompleksna broja (dva para vrijednosti):
2 3
1 4
Upisali ste brojeve
a = 2 + i * 3
b = 1 + i * 4
a je vece ili jednako b!
```

---

## **Zadatak 7.3**

### Korak 1:
* Program stvara niz kompleksnih brojeva, ispisuje ih u tekstualnu datoteku "kompleks.txt" i binarnu datoteku "kompleks.bin".

### Korak 2:
* Otvaraju se datoteke "kompleks.txt" i "kompleks.bin" u notepadu. Iz sadržaja se zaključuje kako su podaci zapravo binarni u "kompleks.bin", a u "kompleks.txt" su čitljivi tekstualni brojevi.

### Korak 3:
* Program mjeri veličinu datoteka na disku. Na temelju toga možemo zaključiti da binarna datoteka zauzima manje prostora jer ne pohranjuje dodatne informacije o formatu.

### Korak 4:
* Program čita sadržaj binarne datoteke "kompleks.bin" u niz objekata klase `kompleks` i ispisuje ih na konzolu.

```cpp
int main() {
    kompleks B[1000];

    // Otvaranje binarne datoteke za čitanje
    ifstream fBin("kompleks.bin", ios::binary);

    // Provjera uspješnosti otvaranja datoteke
    if (!fBin) {
        cerr << "Nemoguće otvoriti binarnu datoteku." << endl;
        return 1;
    }

    // Čitanje sadržaja datoteke u niz objekata kompleks
    fBin.read(reinterpret_cast<char*>(B), 1000 * sizeof(kompleks));

    // Zatvaranje datoteke
    fBin.close();

    // Ispisivanje sadržaja na ekran
    for (int i = 0; i < 1000; i++) {
        cout << B[i] << endl;
    }

    return 0;
}
```

---

# Dodatni zadaci

## **Zadatak 7.4**

```cpp
#include <iostream>
#include <fstream>
#include <string>

int main() {
    std::ifstream inputFile("sample.txt"); // Zamijenjati s imenom stvarne datoteke
    if (!inputFile.is_open()) {
        std::cerr << "Nemoguće otvoriti datoteku." << std::endl;
        return 1;
    }

    std::string line;
    while (std::getline(inputFile, line)) {
        std::cout << line << std::endl;
    }

    inputFile.close();
    return 0;
}
```

Ovaj program otvara datoteku "sample.txt" (promijenite ime prema stvarnom imenu datoteke) i ispisuje njezin sadržaj na konzolu liniju po liniju. Ako datoteka ne može biti otvorena, ispisuje se greška.

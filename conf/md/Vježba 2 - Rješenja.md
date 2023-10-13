## **Zadatak 2.1**

### Korak 1:
Program deklarira varijablu `r` tipa int, dodjeljuje joj vrijednost 2, zatim poziva funkciju `ispisi` koja ispisuje vrijednost `r`. Kompajlirajte program, pokrenite ga i opišite što program radi:

```cpp
#include <iostream>
using namespace std;

void ispisi(int lr) {
    cout << lr << endl;
}

int main() {
    int r;
    r = 2;
    ispisi(r);
    return 0;
}
```

Ovaj program će ispisati:

```
2
```

### Korak 2:
U funkciju `main` dodajte varijablu tipa double, nazivajte je `rDouble`, postavite je na vrijednost 2.7, i pokušajte je ispisati pomoću funkcije `ispisi`. Zašto kompajler javlja upozorenje i ne ispisuje točnu vrijednost?

```cpp
double rDouble = 2.7;
ispisi(rDouble);
```

Kompajler će vjerojatno generirati upozorenje ili grešku jer funkcija `ispisi` očekuje int, a vi pokušavate proslijediti double. Program neće ispisati točnu vrijednost jer će se double implicitno pretvoriti u int, izgubit će se decimalni dio.

### Korak 3:
Dodajte preopterećenu funkciju `ispisi` koja može ispisivati varijable tipa double. Zašto program sada radi?

```cpp
void ispisi(double lrDouble) {
    cout << lrDouble << endl;
}

// ...

ispisi(rDouble);
```

Sada program radi jer smo dodali preopterećenu verziju funkcije `ispisi` koja može raditi s double argumentom.

### Korak 4:
Napišite kod preopterećene funkcije.

```cpp
void ispisi(double lrDouble) {
    cout << lrDouble << endl;
}
```

---

## **Zadatak 2.2**

### Korak 1:
Otvorite datoteku `z221.cpp`, kompajlirajte program i opišite greške koje se pojavljuju i njihov uzrok.

U originalnom kodu, `radijus` u klasi `krug` je privatna varijabla, pa joj ne možemo pristupiti iz `main` funkcije.

### Korak 2:
Promijenite `private:` u `public:`, kompajlirajte program i objasnite zašto sada nema grešaka.

Promjenom `private:` u `public:`, omogućili smo pristup varijabli `radijus` izvan klase, pa sada program kompajlira bez problema.

---

## **Zadatak 2.3**

### Korak 1:
Otvorite datoteku `z231.cpp`, kompajlirajte program i opišite što program radi. Koje sve članove sadrži klasa `krug`?

Program stvara dva objekta klase `krug` (k1 i k2), korisnik unosi radijus za oba kruga, a zatim se ispisuje površina oba kruga.

Članovi klase `krug` su `public: double radijus;` i `double Povrsina();`.

### Korak 2:
Što radi funkcija `Povrsina` klase `krug`? Kako ona može računati pomoću varijable `radijus`, a nismo tu varijablu prenijeli kao argument?

Funkcija `Povrsina` klase `krug` koristi član klase `radijus` za izračun površine kruga. Članovi klase su dostupni unutar metoda klase bez potrebe da se eksplicitno prenose kao argumenti.

### Korak 3:
Definirajte još dva kruga sa imenima `k3` i `k4`. Radijuse im postavite na 2.0 i -2.0. Ispišite površinu tih dvaju krugova. Napišite kod koji ste dodali programu:

```cpp
krug k3;
krug k4;

k3.radijus = 2.0;
k4.radijus = -2.0;

cout << "Povrsina treceg kruga: " << k3.Povrsina() << endl;
cout << "Povrsina cetvrtog kruga: " << k4.Povrsina() << endl;
```

Program će ispisati površine za `k3`, ali za `k4` neće ispravno raditi jer radijus ne može biti negativan.

---

## **Zadatak 2.4**

### Korak 1:
Otvorite datoteku `z241.cpp`, iskompajlirajte program, pokrenite ga i napišite ispis programa.

```cpp
krug k1;
double d;
cout << "Upisite radijus kruga:" << endl;
cin >> d;
k1.SetRadijus(d);
cout << "Radijus kruga je: " << k1.GetRadijus() << endl;
cout << "Povrsina prvog kruga: " << k1.Povrsina() << endl;
```

Program će pitati korisnika da unese radijus, postaviti ga, ispisati ga, zatim ispisati površinu kruga.

### Korak 2:
Ponovo pokrenite program i za radijus upišite negativan broj. Napišite što se događa i zašto.

Program će ispisati poruku "Greska! Radijus ne moze biti negativna vrijednost!" jer je dodan uvjet u funkciji `SetRadijus` koji ne dozvoljava negativne vrijednosti.

### Korak 3:
Zašto u prethodnom koraku, za negativnu vrijednost radijusa, program ispiše da je radijus jednak nuli, iako u funkciji `SetRadijus`, za slučaj negativnog radijusa, radijus nigdje ne postavlja na nulu?

Program će ispisati da je radijus jednak nuli jer u konstruktoru klase `krug` postavlja `radijus` na 0.0. To se događa jer konstruktor automatski poziva prilikom stvaranja objekta.

### Korak 4:
U podrazumijevanom konstruktoru dodajte da se na ekran ispiše „pozvan konstruktor“. Pokrenite program, upišite proizvoljan, pozitivan radijus. Napišite ispis programa.

```cpp
krug k1;
```

Program će ispisati:

```
Upisite radijus kruga:
[unosi korisnik]
Pozvan konstruktor
Radijus kruga je: [vrijednost koju je unio korisnik]
Povrsina prvog kruga: [povrsina izracunata na temelju unesenog radijusa]
```

Temeljem ispisa zaključite i napišite u kojem trenutku se poziva konstruktor:

Konstruktor se poziva prilikom stvaranja objekta, kada se linijom `krug k1;` stvara objekt `k1`.

---

## **Zadatak 2.5**

### Korak 1:
U projektu napravite novu datoteku `z251.cpp` i napišite klasu `razlomak`:

```cpp
#include <iostream>
using namespace std;

class razlomak {
private:
    int brojnik;
    int nazivnik;

public:
    razlomak();
    void Set(int tempBr, int tempNz);
    double GetDecimal();
};

razlomak::razlomak() {
    brojnik = 0;
    nazivnik = 1;
}

void razlomak::Set(int tempBr, int tempNz) {
    if (tempNz != 0) {
        brojnik = tempBr;
        nazivnik = tempNz;
    } else {
        cout << "Greska! Nazivnik ne moze biti jednak nuli!" << endl;
    }
}

double razlomak::GetDecimal() {
    return static_cast<double>(brojnik) / nazivnik;
}

int main() {
    razlomak raz;
    int tempBr, tempNz;

    cout << "Unesite brojnik: ";
    cin >> tempBr;

    cout << "Unesite nazivnik: ";
    cin >> tempNz;

    raz.Set(tempBr, tempNz);

    cout << "Decimalna vrijednost razlomka: " << raz.GetDecimal() << endl;

    return 0;
}
```

### Korak 2:
Definirajte objekt `raz` klase `razlomak`, učitajte vrijednost brojnika i nazivnika s tipkovnice, postavite ih pomoću funkcije `Set`, a zatim ispišite decimalnu vrijednost razlomka pomoću funkcije `GetDecimal`.

```cpp
razlomak raz;
int tempBr, tempNz;

cout << "Unesite brojnik: ";
cin >> tempBr;

cout << "Unesite nazivnik: ";
cin >> tempNz;

raz.Set(tempBr, tempNz);

cout << "Decimalna vrijednost razlomka: " << raz.GetDecimal() << endl;
```

---

# **Dodatni zadaci**

## **Zadatak 2.6**

### Korak 1:
Otvorite datoteku `z261.cpp`, pokrenite program i napišite ispis.

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string naziv = "Objektno orijentirano programiranje";

    cout << naziv << endl;
    cout << "Duljina stringa je: " << naziv.length() << endl;

    return 0;
}
```

Program će ispisati:

```
Objektno orijentirano programiranje
Duljina stringa je: 30
```

Opišite što program radi:

Program definira string `naziv`, ispisuje ga, a zatim ispisuje duljinu stringa.

### Korak 2:
Deklarirajte još jedan objekt klase `string`, naziva `proba`. Nakon toga učitajte objekt `proba` s tipkovnice pomoću operatora `>>`. Koristeći metodu `length()` string klase, ispišite duljinu stringa `proba`.

```cpp
string proba;
cout << "Unesite string za probu: ";
cin >> proba;

cout << "Duljina stringa 'proba' je: " << proba.length() << endl;
```

### Korak 3:
Gledajući kod zadatka, zaključite koja je razlika između korištenja varijable određenog tipa i objekta određene klase?

Razlika između korištenja varijable određenog tipa i objekta određene klase je u tome što objekt klase može sadržavati dodatne metode i funkcionalnosti koje su specifične za tu klasu. U ovom primjeru, klasa `string` ima metodu `length()` koja vraća duljinu stringa, dok varijabla određenog tipa to ne bi imala. Objekti klase imaju metode i članove koji su specifični za tu klasu, dok varijable određenog tipa obično nemaju dodatne funkcionalnosti.

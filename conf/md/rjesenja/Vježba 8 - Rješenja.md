## **Zadatak 8.1**

### Korak 1:
```cpp
#include <iostream>
#include "tstring.h"
using namespace std;

int main(void)
{
    // deklaracija stringova u C stilu
    char ime[50] = "Ivan";
    char prezime[50] = "Peras";
    char imeIPrezime[100] = "";
    char kopija[100] = "";

    // deklaracija stringova u C++ stilu
    TString TSIme = "Ivan";
    TString TSPrezime = "Peras";
    TString TSImeIPrezime = "";
    TString TSKopija = "";

    cout << "Kopiranje:" << endl;
    
    // kopiranje u C stilu
    strcpy(imeIPrezime, ime);
    cout << "C: " << imeIPrezime << endl;

    // kopiranje u C++ stilu
    TSImeIPrezime = TSIme;
    cout << "C++: " << TSImeIPrezime << endl << endl;

    cout << "Spajanje:" << endl;

    // spajanje u C stilu
    strcat(imeIPrezime, " ");
    strcat(imeIPrezime, prezime);
    cout << "C: " << imeIPrezime << endl;

    // spajanje u C++ stilu
    TSImeIPrezime = TSImeIPrezime + " " + TSPrezime;
    cout << "C++: " << TSImeIPrezime << endl << endl;

    cout << "Mjerenje duljine:" << endl;

    // mjerenje duljine u C stilu
    cout << "C: " << strlen(imeIPrezime) << endl;

    // mjerenje duljine u C++ stilu
    cout << "C++: " << TSImeIPrezime.length() << endl << endl;

    cout << "Usporedba:" << endl;

    // usporedba u C stilu
    cout << "C: " << !strcmp(imeIPrezime, ime) << endl;

    // usporedba u C++ stilu
    cout << "C++: " << (TSImeIPrezime == TSIme) << endl << endl;

    return 0;
}
```

Ispis:

```
Kopiranje:
C: Ivan
C++: Ivan

Spajanje:
C: Ivan Peras
C++: Ivan Peras

Mjerenje duljine:
C: 12
C++: 12

Usporedba:
C: 0
C++: 1
```

### Korak 2:
Usporedite rad s stringovima u C i C++. Evo nekoliko razmatranja:

1. **Čitljivost koda:**
   - C++ koristi objekte klase `string`, što čini kod čišćim i čitljivijim. Na primjer, `TSImeIPrezime = TSIme;` jasnije prenosi značenje od `strcpy(imeIPrezime, ime);`.

2. **Dinamičko upravljanje memorijom:**
   - U C++ stilu, objekti klase `string` dinamički upravljaju svojom memorijom. To znači da se ne morate brinuti o alociranju i dealociranju memorije, za razliku od C stila gdje je potrebno ručno upravljati memorijom.

3. **Operatori:**
   - C++ omogućuje korištenje operatora `+` za spajanje stringova, dok u C stilu to radimo s funkcijom `strcat`. Ovo čini kôd jednostavnijim i čitljivijim.

4. **Duljina stringa:**
   - U C stilu, mjerenje duljine stringa obavlja se funkcijom `strlen`, dok se u C++ koristi metoda `length()`. Metoda `length()` u C++-u je često smatrana sigurnijom i jednostavnijom.

5. **Usporedba stringova:**
   - U C++ koristimo operatore za usporedbu, kao što je `==`. U C stilu, koristimo funkciju `strcmp`. Operatori u C++-u pružaju čišći i čitljiviji način usporedbe.

**C++ pruža apstrakciju i sučelje koje čini rad s stringovima sigurnijim i jednostavnijim, uz manje brige o detaljima implementacije.**

---

## **Zadatak 8.2**

```cpp
#include <iostream>
#include <string>
using namespace std;

int main()
{
    string unos;
    cout << "Unesite string: ";
    getline(cin, unos);

    string podstring;
    cout << "Unesite podstring za traženje: ";
    cin >> podstring;

    size_t pozicija = unos.find(podstring);

    if (pozicija != string::npos)
    {
        cout << "Podstring pronađen na poziciji: " << pozicija << endl;
    }
    else
    {
        cout << "Podstring nije pronađen." << endl;
    }

    return 0;
}
```

---

## **Zadatak 8.3**

### Korak 1:
```cpp
#include <iostream>
#include "tvector.h"
using namespace std;

int main()
{
    tvector<double> vec;
    double val;
    cout << "Unos proizvoljnog niza brojeva u vektor." << endl;
    cout << "Unos zavrsava kada se otkuca neko slovo!" << endl;

    while (cin >> val)
    {
        vec.push_back(val);
    }

    double sum = 0;
    for (int i = 0; i < vec.size(); i++)
    {
        sum += vec[i];
    }

    double avg = sum / vec.size();
    cout << "Suma od " << vec.size() << " elemenata: " << sum << ". Srednja vrijednost: " << avg << endl;

    return 0;
}
```

Ispis:
```
Uneseni brojevi: 10 20 30 40 50
Suma od 5 elemenata: 150. Srednja vrijednost: 30
```

### Korak 2:
```cpp
#include <iostream>
#include <vector>
#include "tvector.h"
using namespace std;

int main()
{
    tvector<double> vec;
    double val;
    cout << "Unos proizvoljnog niza brojeva u vektor." << endl;
    cout << "Unos zavrsava kada se otkuca neko slovo!" << endl;

    while (cin >> val)
    {
        vec.push_back(val);
    }

    tvector<double> revVec;

    for (int i = vec.size() - 1; i >= 0; i--)
    {
        revVec.push_back(vec[i]);
    }

    double sum = 0;
    for (int i = 0; i < vec.size(); i++)
    {
        sum += vec[i];
    }

    double avg = sum / vec.size();
    cout << "Suma od " << vec.size() << " elemenata: " << sum << ". Srednja vrijednost: " << avg << endl;

    cout << "Sadržaj vektora revVec (obrnuti redoslijed): ";
    for (int i = 0; i < revVec.size(); i++)
    {
        cout << revVec[i] << " ";
    }
    cout << endl;

    return 0;
}
```

Uneseni vektori:
``` cpp
vec[0] 17
vec[1] 32
vec[2] 18
vec[3] 3
revVec[0] 3
revVec[1] 18
revVec[2] 32
revVec[3] 17
```

### Korak 3:
```
Suma od 5 elemenata: 150. Srednja vrijednost: 30
Sadržaj vektora revVec (obrnuti redoslijed): 50 40 30 20 10
```

---

## **Zadatak 8.4**

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main()
{
    vector<int> vektor;

    // Promijenite veličinu vektora prema korisnikovom unosu
    int velicina;
    cout << "Unesite veličinu vektora: ";
    cin >> velicina;
    vektor.resize(velicina);

    // Unesite vrijednosti na željene pozicije u vektoru
    int pozicija, vrijednost;

    cout << "Unesite poziciju i vrijednost (prestani unositi kada uneseš slovo): " << endl;
    while (cin >> pozicija >> vrijednost)
    {
        if (pozicija < 0 || pozicija >= vektor.size())
        {
            cout << "Neispravna pozicija. Unesite ponovo." << endl;
            continue;
        }

        vektor[pozicija] = vrijednost;
    }

    // Ispis vektora
    cout << "Vektor nakon unosa:" << endl;
    for (int i = 0; i < vektor.size(); i++)
    {
        cout << vektor[i] << " ";
    }
    cout << endl;

    return 0;
}
```

---

## **Zadatak 8.5**

### Korak 1:

Ovaj program definira predložak funkcije `maximum`, koji uspoređuje dvije vrijednosti i vraća veću od njih. Funkcija `maximum` je napisana kao predložak (template) funkcija.

Ova funkcija `maximum` je generička, što znači da može raditi s različitim tipovima podataka. Funkcija uzima dva argumenta tipa `T` i vraća veći od njih.

### Korak 2:

```cpp
#include <iostream>
using namespace std;

template <class T>
T maximum(T a, T b)
{
    if (a > b)
    {
        return a;
    }
    else
    {
        return b;
    }
}

template <class T>
T absolute(T value)
{
    return (value < 0) ? -value : value;
}

int main()
{
    int a = 3, b = 5;
    double c = 3.1, d = 5.2;

    cout << "Maximum of " << a << " and " << b << ": " << maximum(a, b) << endl;
    cout << "Maximum of " << c << " and " << d << ": " << maximum(c, d) << endl;

    cout << "Absolute value of " << a << ": " << absolute(a) << endl;
    cout << "Absolute value of " << c << ": " << absolute(c) << endl;

    return 0;
}
```

---

# Dodatni zadaci

## **Zadatak 8.6**

```cpp
#include <iostream>
#include <string>
using namespace std;

bool isPalindrom(string str)
{
    int i = 0;
    int j = str.length() - 1;

    while (i < j)
    {
        if (str[i] != str[j])
        {
            return false;
        }
        i++;
        j--;
    }
    return true;
}

int main()
{
    string input;
    cout << "Unesite string: ";
    cin >> input;

    if (isPalindrom(input))
    {
        cout << "String je palindrom." << endl;
    }
    else
    {
        cout << "String nije palindrom." << endl;
    }

    return 0;
}
```

Ovaj program koristi petlju koja prolazi kroz string s oba kraja i uspoređuje znakove kako bi provjerio je li string palindrom.
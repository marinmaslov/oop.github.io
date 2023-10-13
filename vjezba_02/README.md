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
      return 0;
  }
  ```

---

Ovi osnovni koncepti u C++-u, kao što su preopterećene funkcije, klase i objekti te klasa `string`, pružaju moćne alate za strukturiranje i organiziranje koda u objektno orijentiranom programiranju.

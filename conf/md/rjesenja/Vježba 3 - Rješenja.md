## **Zadatak 3.1**

### Korak 1:
- **Razlika između funkcije `povrsinaVrijednost` i `povrsinaPokazivac`:**
  - Funkcija `povrsinaVrijednost` vraća rezultat kao vlastitu vrijednost, tj. koristi se prijenosom po vrijednosti.
  - Funkcija `povrsinaPokazivac` koristi prijenos po pokazivaču kako bi rezultat vratila putem pokazivača.

### Korak 2:
*Promjene u programu:*

- **Dodana funkcija `povrsinaReferenca`:**
  ```cpp
  void povrsinaReferenca(double lr, double& ref) {
      ref = lr * lr * 3.14;
  }
  ```

### Korak 3:
- **Dodana funkcija `povrsinaOpseg`:**
  ```cpp
  void povrsinaOpseg(double lr, double& povrsina, double& opseg) {
      povrsina = lr * lr * 3.14;
      opseg = 2 * lr * 3.14;
  }
  ```

*Poziv funkcije `povrsinaOpseg` u glavnom programu:*
```cpp
double pov, op;
povrsinaOpseg(r, pov, op);
cout << "Povrsina kruga = " << pov << " m2, Opseg kruga = " << op << " m" << endl;
```

### Korak 4:
- **Može li se funkcija iz prethodnog koraka realizirati prijenosom argumenata isključivo po vrijednosti?**
  - Ne, jer funkcija treba vratiti dvije vrijednosti (površinu i opseg) putem referenci, a prijenos po vrijednosti ne podržava povrat više od jedne vrijednosti.

```
Tips&Tricks: Odgovor je zapravo da može, ako koristimo neku od odgovarajućih struktura podataka.
```

---

## **Zadatak 3.2**

### Korak 1:
- **Ispis programa:**
  ```
  0
  1
  1
  2
  ```

### Korak 2:
Kako bi mogli i poziv po vrijednosti `FunctionByValue` iskoristiti za povećanje varijable i.**

- Da bismo iskoristili poziv po vrijednosti `FunctionByValue` za povećanje varijable `i`, trebamo koristiti povratnu vrijednost funkcije i pridružiti je varijabli `i` u glavnom programu.
- Promijenite funkciju `FunctionByValue` tako da vraća novu vrijednost, tj. povećanu vrijednost `i`. Na primjer:
  ```cpp
  int FunctionByValue(int iVal) { return iVal + 1; }
  ```
- U glavnom programu koristite ovu funkciju na sljedeći način:
  ```cpp
  i = FunctionByValue(i);
  ```
- Ovim postupkom, dobivate povećanu vrijednost varijable `i` nakon poziva funkcije s pozivom po vrijednosti.    ```

---

## **Zadatak 3.3**

### Korak 1:
- **Pogreška u programu:**
  - Funkcija `rect_area` koristi prijenos po vrijednosti za parametar `larea`, pa kad se promijeni unutar funkcije, to ne utječe na varijablu `area` u funkciji `main`.

*Rješenje:*
- Umjesto prijenosa po vrijednosti, trebamo koristiti prijenos po referenci za `larea`:
  ```cpp
  void rect_area(float lwidth, float lheight, float& larea) {
      larea = lwidth * lheight;
      cout << "The area in the function is " << larea << endl;
  }
  ```

---

## **Zadatak 3.4**

- **Funkcije za računanje opsega likova:**
  ```cpp
  void opsegTrokuta(float a, float b, float c, float& opseg) {
      opseg = a + b + c;
  }

  void opsegKvadrata(float a, float& opseg) {
      opseg = 4 * a;
  }

  void opsegKruga(float r, float& opseg) {
      opseg = 2 * 3.14 * r;
  }
  ```

- **Pozivi funkcija u glavnom programu:**
```cpp
float opseg;

opsegTrokuta(3, 4, 5, opseg);
cout << "Opseg trokuta: " << opseg << endl;

opsegKvadrata(2, opseg);
cout << "Opseg kvadrata: " << opseg << endl;

opsegKruga(1.5, opseg);
cout << "Opseg kruga: " << opseg << endl;
```

---

# **Dodatni zadaci**

## **Zadatak 3.5**

- Implementacija klase `Registracija`:
```cpp
#include <iostream>
using namespace std;

class Registracija {
private:
    int reg1;
    int reg2;

public:
    Registracija() : reg1(100), reg2(100) {}

    void Set(int temp1, int temp2) {
        if (temp1 >= 100 && temp1 <= 999 && temp2 >= 100 && temp2 <= 999) {
            reg1 = temp1;
            reg2 = temp2;
        }
    }

    void Ispisi() {
        cout << reg1 << "-" << reg2 << endl;
    }
};

int main() {
    Registracija r;
    r.Set(534, 234);
    r.Ispisi();

    return 0;
}
```

*Objašnjenje:*
- Klasa `Registracija` ima dvije privatne varijable `reg1` i `reg2` koje čine registraciju.
- Default konstruktor postavlja objekt na početnu vrijednost `100-100`.
- Funkcija `Set` postavlja vrijednosti registracije pod određenim uvjetima.
- Funkcija `Ispisi` ispisuje formatiranu registraciju.

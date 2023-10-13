# Vježba 3 - Pokazivači i reference, prijenos argumenata

## **1. Pokazivači i Reference**

### **1.1 Pokazivači:**
   - **Definicija:** Pokazivač je varijabla koja sadrži memorijsku adresu neke druge varijable.
   - **Declaracija i Inicijalizacija:**
     ```cpp
     int* p;  // Deklaracija pokazivača na cjelobrojni tip podataka
     int x = 5;
     p = &x;  // Inicijalizacija pokazivača s adresom varijable x
     ```
   - **Dereferenciranje:**
     ```cpp
     cout << *p;  // Ispisuje vrijednost varijable na koju pokazuje p (u ovom slučaju, 5)
     ```

## **1.2 Reference:**
   - **Definicija:** Referenca je drugo ime za već postojeću varijablu.
   - **Deklaracija i Inicijalizacija:**
     ```cpp
     int y = 10;
     int& r = y;  // Referenca r sada referencira varijablu y
     ```
   - **Upotreba:**
     ```cpp
     cout << r;  // Ispisuje vrijednost varijable y preko reference r
     ```

---

## **2. Prijenos Argumenata**

### **2.1 Prijenos po Vrijednosti:**
   - **Karakteristike:**
     - Vrijednost varijable se kopira, originalna varijabla ostaje nepromijenjena.
     - U funkciji se radi s kopijom varijable.

   - **Primjer:**
     ```cpp
     void funkcijaVrijednost(int x) {
       x = x + 1;
     }

     int main() {
       int a = 5;
       funkcijaVrijednost(a);
       cout << a;  // Ispisuje 5 jer je funkcija radila s kopijom a.
     }
     ```

#### **2.1.1 Prijenos po Vrijednosti s Povratom:**
   - **Karakteristike:**
     - Funkcija vraća rezultat, ali originalna varijabla ostaje nepromijenjena.

   - **Primjer:**
     ```cpp
     int funkcijaVracanjeVrijednosti(int x) {
       return x + 1;
     }

     int main() {
       int d = 5;
       d = funkcijaVracanjeVrijednosti(d);
       cout << d;  // Ispisuje 6 jer je funkcija vratila rezultat koji smo dodijelili varijabli d.
     }
     ```

### **2.2 Prijenos po Pokazivaču:**
   - **Karakteristike:**
     - Funkcija prima memorijsku adresu varijable.
     - Funkcija može mijenjati originalnu varijablu preko pokazivača.

   - **Primjer:**
     ```cpp
     void funkcijaPokazivac(int* p) {
       (*p) = (*p) + 1;
     }

     int main() {
       int b = 5;
       funkcijaPokazivac(&b);
       cout << b;  // Ispisuje 6 jer je funkcija promijenila vrijednost varijable b.
     }
     ```


#### **2.2.1 Prijenos po Pokazivaču s Povratom:**
   - **Karakteristike:**
     - Funkcija vraća rezultat, može mijenjati originalnu varijablu preko pokazivača.

   - **Primjer:**
     ```cpp
     int funkcijaVracanjePokazivac(int* p) {
       (*p) = (*p) + 1;
       return (*p);
     }

     int main() {
       int e = 5;
       e = funkcijaVracanjePokazivac(&e);
       cout << e;  // Ispisuje 6 jer je funkcija promijenila vrijednost varijable e i vratila rezultat.
     }
     ```


### **2.3 Prijenos po Referenci:**
   - **Karakteristike:**
     - Funkcija prima referencu na varijablu.
     - Funkcija može mijenjati originalnu varijablu preko reference.

   - **Primjer:**
     ```cpp
     void funkcijaReferenca(int& r) {
       r = r + 1;
     }

     int main() {
       int c = 5;
       funkcijaReferenca(c);
       cout << c;  // Ispisuje 6 jer je funkcija promijenila vrijednost varijable c.
     }
     ```

#### **2.3.1 Prijenos po Referenci s Povratom:**
   - **Karakteristike:**
     - Funkcija vraća rezultat, može mijenjati originalnu varijablu preko reference.

   - **Primjer:**
     ```cpp
     int funkcijaVracanjeReferenca(int& r) {
       r = r + 1;
       return r;
     }

     int main() {
       int f = 5;
       f = funkcijaVracanjeReferenca(f);
       cout << f;  // Ispisuje 6 jer je funkcija promijenila vrijednost varijable f i vratila rezultat.
     }
     ```

---

Ovi primjeri pokazuju različite načine kako se argumenti mogu prenositi u funkcije u C++. Svi ovi pristupi imaju svoje specifične situacije u kojima se preporučuju.

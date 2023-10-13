# Vježba 8 - Stringovi i generičko programiranje


## 1. Stringovi u `c++`-u

### 1.1 Uvod u Stringove u C++

U C++, stringovi se mogu manipulirati na nekoliko načina. Osnovni oblik stringa u C stilu koristi se s poljem znakova (`char`). Međutim, C++ također pruža svoju klasu za rad s tekstualnim podacima, a to je `std::string`. 

   ```cpp
   #include <iostream>
   #include <cstring> // Za rad s C stilskim stringovima

   using namespace std;

   int main() {
       // C stilski string
       char ime[50] = "John";

       // C++ string
       string cppIme = "John";

       cout << "C stilski string: " << ime << endl;
       cout << "C++ string: " << cppIme << endl;

       return 0;
   }
   ```

### 1.2 Operacije nad Stringovima

Rad s stringovima u C++ pruža brojne prednosti. Na primjer, kopiranje, spajanje i mjerenje duljine stringa.

   ```cpp
   #include <iostream>
   #include <cstring>
   #include <string>

   using namespace std;

   int main() {
       string ime = "John";
       string prezime = "Doe";

       // Kopiranje stringova
       string punoIme = ime;
       cout << "Kopirano ime: " << punoIme << endl;

       // Spajanje stringova
       punoIme = ime + " " + prezime;
       cout << "Spojeno ime i prezime: " << punoIme << endl;

       // Mjerenje duljine stringa
       cout << "Duljina stringa: " << punoIme.length() << endl;

       return 0;
   }
   ```

### 1.3 Usporedba Stringova

Usporedba stringova može se izvršiti pomoću usporedbe C stilskih stringova (`strcmp`) ili operatora usporedbe C++ stringova (`==`).

   ```cpp
   #include <iostream>
   #include <cstring>
   #include <string>

   using namespace std;

   int main() {
       string ime1 = "John";
       string ime2 = "Doe";
       string punoIme1 = "John Doe";
       string punoIme2 = "John Doe";

       // Usporedba C stilskim stringom
       if (strcmp(ime1.c_str(), ime2.c_str()) == 0) {
           cout << "Imena su jednaka (C stil)" << endl;
       } else {
           cout << "Imena nisu jednaka (C stil)" << endl;
       }

       // Usporedba C++ stringom
       if (punoIme1 == punoIme2) {
           cout << "Puna imena su jednaka (C++ stil)" << endl;
       } else {
           cout << "Puna imena nisu jednaka (C++ stil)" << endl;
       }

       return 0;
   }
   ```

## 2. Generičko Programiranje u `C++`-u

Generičko programiranje omogućuje pisanje funkcija i klasa koje rade s različitim tipovima podataka. To se postiže pomoću predložaka (templates). Predlošci u C++ omogućuju stvaranje općih funkcija ili klasa koje rade s različitim tipovima podataka bez potrebe za pisanjem posebnog koda za svaki tip.

Primjer:

   ```cpp
   #include <iostream>
   using namespace std;

   // Primjer generičke funkcije za pronalaženje maksimuma
   template <class T>
   T maximum(T a, T b) {
       return (a > b) ? a : b;
   }

   int main() {
       int broj1 = 5, broj2 = 10;
       double decimalni1 = 3.14, decimalni2 = 2.71;

       cout << "Maksimum od brojeva: " << maximum(broj1, broj2) << endl;
       cout << "Maksimum od decimalnih brojeva: " << maximum(decimalni1, decimalni2) << endl;

       return 0;
   }
   ```

Funkcija `maximum` može se koristiti s bilo kojim tipom podataka koji podržava operator usporedbe `>`.

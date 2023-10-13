# Vježba 4 - Konstruktori, destruktori, inline i friend funkcije

## 1. Konstruktori i Destruktori

### 1.1 Konstruktori
- **Definicija:** Konstruktori su posebne metode klase koje se automatski pozivaju prilikom stvaranja objekta.
- **Sintaksa:** 
  ```cpp
  class MyClass {
  public:
      // Default konstruktor
      MyClass() {
          // tijelo konstruktora
      }

      // Konstruktor s parametrima
      MyClass(int x, int y) {
          // tijelo konstruktora
      }
  };
  ```
- **Primjena:** Konstruktori omogućuju inicijalizaciju objekta kada se stvara.
- **Napomena:** Kao i funkcije/metode, konstruktori se mogu preopterećivati!

### 1.2 Destruktori
- **Definicija:** Destruktori su metode članice koje se automatski pozivaju kada objekt izlazi iz opsega ili se ručno uništava.
- **Sintaksa:**
  ```cpp
  class MyClass {
  public:
      // Destruktor
      ~MyClass() {
          // tijelo destruktora
      }
  };
  ```
- **Primjena:** Destruktori koriste se za čišćenje resursa alociranih tijekom života objekta.

---

## 2. Inline i Friend Funkcije

### 2.1 Inline Funkcije
- **Definicija:** Inline funkcije su male funkcije čiji se kod umetne direktno na mjesto poziva kako bi se smanjilo vrijeme izvršavanja.
- **Sintaksa:**
  ```cpp
  class MyClass {
  public:
      // Inline funkcija
      inline void myFunction() {
          // tijelo funkcije
      }
  };
  ```
- **Primjena:** Inline funkcije smanjuju overhead poziva funkcija, ali trebaju se koristiti s oprezom zbog povećanja veličine koda.

### 2.2 Friend Funkcije
- **Definicija:** Friend funkcije imaju pristup privatnim i zaštićenim članovima klase, ali nisu metode klase.
- **Sintaksa:**
  ```cpp
  class MyClass {
  private:
      int myVar;

  public:
      // Deklaracija friend funkcije
      friend void friendFunction(MyClass obj);
  };
  
  // Definicija friend funkcije
  void friendFunction(MyClass obj) {
      cout << obj.myVar;
  }
  ```
- **Primjena:** Friend funkcije omogućuju vanjskim funkcijama pristup internim detaljima klase.

---

## 3. Operatori i Prioriteti

### 3.1 Operatori
- **Definicija:** Operatori su simboli koji izvršavaju određene operacije nad operandima.
- **Primjeri:**
  - Aritmetički: `+`, `-`, `*`, `/`, `++`, `--`
  - Relacijski: `==`, `!=`, `<`, `>`, `<=`, `>=`
  - Logički: `&&`, `||`, `!`
- **Primjena:** Operatori omogućuju izvođenje različitih operacija nad podacima.

### 3.2 Prioriteti
- **Definicija:** Prioritet operacija određuje redoslijed izvršavanja izraza.
- **Primjeri:**
  - Aritmetički: `*` i `/` imaju viši prioritet od `+` i `-`
  - Zagrade mijenjaju prioritet
- **Primjena:** Razumijevanje prioriteta pomaže u napisanju jasnog i preciznog koda.

Evo nekoliko općih pravila prioriteta operatora u jeziku C++:

1. **Postfiksni i prefiksni operatori inkrementa/dekrementa:**
   - `++x`, `--x` (prefiksni)
   - `x++`, `x--` (postfiksni)

2. **Aritmetički operatori:**
   - `*` (množenje), `/` (dijeljenje), `%` (modulo)
   - `+` (zbrajanje), `-` (oduzimanje)

3. **Odnosni operatori:**
   - `<`, `<=`, `>`, `>=`

4. **Jednakosni operatori:**
   - `==`, `!=`

5. **Logički operatori:**
   - `&&` (logičko "i")
   - `||` (logičko "ili")

6. **Pridruživanje:**
   - `=`, `+=`, `-=`, `*=`, `/=`, `%=` itd.

7. **Zarezni operator:**
   - `,` (koristi se za odvajanje izraza)

Primjer sa zagradama:
```cpp
int result = (a + b) * c;
```

U ovom izrazu, zbrajanje (`+`) između `a` i `b` ocjenjuje se prije množenja (`*`), jer su zagrada postavljena oko tog dijela izraza.

---

## 4. Casting u C++

### 4.1 Static Cast
- **Definicija:** `static_cast` koristi se za sigurno pretvaranje tipova.
- **Sintaksa:**
  ```cpp
  double myDouble = 3.14;
  int myInt = static_cast<int>(myDouble);
  ```
- **Primjena:** `static_cast` povećava sigurnost pretvaranja tipova.

### 4.2 C-Style Cast
- **Definicija:** C-Style cast je stariji stil castanja prisutan i u C++.
- **Sintaksa:**
  ```cpp
  double myDouble = 3.14;
  int myInt = (int)myDouble;
  ```
- **Primjena:** C-Style cast može izazvati probleme ako se koristi nepažljivo.

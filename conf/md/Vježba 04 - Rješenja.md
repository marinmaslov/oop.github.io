## **Zadatak 4.1**

### Korak 1:
Program definira klasu `Krug` koja ima privatnu varijablu `radijus`, te javne funkcije `SetRadijus`, `izracunajOpseg` i `izracunajPovrsinu`. U glavnoj funkciji, stvara se objekt klase `Krug`, postavlja mu se radijus na 1.0, te se ispisuju površina i opseg kruga. 

```cpp
Povrsina: 3.14
Opseg: 6.28
```

Program stvara objekt `Krug`, postavlja mu radijus, te izračunava i ispisuje površinu i opseg kruga. 

### Korak 2:
Dodan je novi konstruktor koji prima radijus kao argument i postavlja ga na tu vrijednost.

```cpp
Krug::Krug(double r) {
    radijus = (r >= 0.0) ? r : 0.0;
}
```

### Korak 3:
U glavnoj funkciji, umjesto prve dvije linije, koristi se novi konstruktor za inicijalizaciju objekta.

```cpp
Krug k(1.0); // Stvaranje objekta s radijusom 1.0 putem novog konstruktora
```

---

## **Zadatak 4.2**

### Korak 1:
Dodan je destruktor koji ispisuje "Odoh ja!" kada se objekt uništi.

```cpp
Krug::~Krug() {
    cout << "Odoh ja!" << endl;
}
```

### Korak 2:
Program ispisuje:

```cpp
Povrsina: 3.14
Opseg: 6.28
Odoh ja!
```

Destruktor se poziva kada objekt izlazi iz opsega njegove vidljivosti, tj. kada se program završi.

---

## **Zadatak 4.3**

### Korak 1:
Napravljena je nova datoteka `z431.cpp` u kojoj je definirana klasa `tocka` s propisanim funkcijama.

```cpp
class tocka {
	private: double x, y; // Privatne varijable koordinate točke 
	
	public:
		// Default konstruktor postavlja koordinate na (0, 0)
		tocka() : x(0.0), y(0.0) {}
		
		// Konstruktor s argumentima postavlja koordinate na dane vrijednosti
		tocka(double _x, double _y) : x(_x), y(_y) {}
		
		// Funkcija za računanje udaljenosti između dvije točke
		double Udaljenost(tocka t) {
			return sqrt(pow(x - t.x, 2) + pow(y - t.y, 2));
		}
};
```

U main funkciji stvoreni su objekti `t1` i `t2`, te je ispisana udaljenost između njih.

```cpp
int main() {
	// Deklaracija i inicijalizacija objekata klase tocka
	tocka t1(1.4, 4.3);
	tocka t2(5.7, -3.8);
	
	// Ispisivanje udaljenosti između točaka
	cout << "Udaljenost između t1 i t2: " << t1.Udaljenost(t2) << endl;
	return 0;
}
```

---

## **Zadatak 4.4**

### Korak 1:
Konstruktor klase `tocka` je pretvoren u inline funkciju. To znači da će se kod konstruktora umetnuti direktno tamo gdje se poziva.

```cpp
inline Tocka() : x(0.0), y(0.0) {}
```

Prednosti inline funkcija su ubrzanje izvođenja programa jer se ne mora ići do funkcije, nego se njen kod direktno ubacuje na mjesto gdje se poziva.

### Korak 2:
Funkcija `Udaljenost` je prebačena iz klase i definirana kao friend funkcija.

```cpp
class tocka {
	private:
	    double x, y;
	
	public:
	    tocka() : x(0.0), y(0.0) {}
	    tocka(double _x, double _y) : x(_x), y(_y) {}
	
	    // Deklaracija friend funkcije
	    friend double Udaljenost(tocka t1, tocka t2);
};

// Definicija friend funkcije izvan klase
double Udaljenost(tocka t1, tocka t2) {
    return sqrt(pow(t1.x - t2.x, 2) + pow(t1.y - t2.y, 2));
}
```

### Korak 3:
Prijenos argumenata po referenci u funkciji `Udaljenost` može biti brži jer se ne kopiraju kompletni objekti, nego se samo proslijede adrese. No, to može značiti i da se originalni objekti mogu promijeniti.

---

# **Dodatni Zadaci**

## **Zadatak 4.5**

### Korak 1:
Program generira sljedeći ispis:

```cpp
0
0
1
```

### Korak 2:
Prioriteti koraka:

1. i++
2. i - a
3. b = 0
4. (i - a) == b

---

## **Zadatak 4.6**

### Korak 1:
Djeljenje ne daje točan rezultat jer su `i1` i `i2` cjelobrojni brojevi, pa je rezultat cjelobrojno djeljenje.

### Korak 2:
Ispravak programa pomoću operatora pretvorbe tipova:

```cpp
f1 = (float)i1 / (float)i2;
```

Program ispisuje:

```cpp
funkcija: f1=2.5
```

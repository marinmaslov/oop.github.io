## **Zadatak 5.1**

### Korak 1:
- Varijabla `x` je globalna jer je definirana izvan funkcija i dostupna je svugdje u programu.
- Varijabla `y` je lokalna jer je definirana unutar funkcije `fun`.
- Varijabla `z` je statička (static) varijabla. Statičke varijable imaju doseg unutar funkcije ili bloka, ali zadržavaju svoju vrijednost između poziva funkcija. Dakle, `z` je statička varijabla lokalna za funkciju `fun`, ali ima trajni doseg. 

### Korak 2:
Greška će se javiti jer u funkciji `main`, nakon poziva funkcije `fun`, pokušavate pristupiti varijablama `y` i `z` koje su definirane unutar funkcije `fun` i stoga nisu dostupne izvan te funkcije.

### Korak 3:
Doseg i vrijeme trajanja varijabli:
   - Globalna varijabla `x`: Doseg je globalan, vrijeme trajanja je tijekom cijelog programa.
   - Lokalna varijabla `y` u funkciji `fun`: Doseg je unutar funkcije `fun`, vrijeme trajanja je tijekom izvršavanja te funkcije.
   - Statička varijabla `z` u funkciji `fun`: Doseg je unutar funkcije `fun`, vrijeme trajanja je tijekom cijelog programa.

---

## **Zadatak 5.2**

### Korak 1:
Program stvara objekt klase `Krug`, postavlja mu radijus na 1.0 pomoću pristupnika, te izračunava površinu i opseg kruga. Zatim ispisuje rezultate.

### Korak 2:
Alokacija i dealokacija memorije:
   - Alokacija: `Krug *k = new Krug();`
   - Dealokacija: `delete k;`

### Korak 4:
Pozivi funkcija:
   - `k->postaviRadijus(1.0);`
   - `cout << "Povrsina: " << k->izracunajPovrsinu() << endl;`
   - `cout << "Opseg: " << k->izracunajOpseg() << endl;`

### Korak 5:
Funkcija `delete` automatski poziva destruktor klase.

### Korak 6:
Dodavanje destruktora:
```cpp
Krug::~Krug() {
    cout << "Pozvan destruktor!" << endl;
}
```

---

## **Zadatak 5.3**

### Korak 1:
Program inicijalizira niz, ispisuje njegov sadržaj te računa i ispisuje sumu elemenata.

### Korak 2 i 3:
Objektno orijentirani oblik:
```cpp
class klNiz {
private:
    int iA[10];
public:
    klNiz() {
        for (int i = 0; i < 10; i++)
            iA[i] = 2 * i;
    }
    int sumaNiza() {
        int s = 0;
        for (int i = 0; i < 10; i++)
            s += iA[i];
        return s;
    }
};

int main() {
    klNiz obj;
    cout << "Suma niza je:" << obj.sumaNiza() << endl;
    return 0;
}
```

---

## **Zadatak 5.4**

```cpp
class klNiz {
private:
    int *iA;
public:
    klNiz() {
        iA = new int[10];
        for (int i = 0; i < 10; i++)
            iA[i] = 2 * i;
    }
    ~klNiz() {
        delete[] iA;
    }
    int sumaNiza() {
        int s = 0;
        for (int i = 0; i < 10; i++)
            s += iA[i];
        return s;
    }
};

int main() {
    klNiz obj;
    cout << "Suma niza je:" << obj.sumaNiza() << endl;
    return 0;
}
```

---

# **Dodatni zadaci**

## **Zadatak 5.5**

```cpp
class Krug {
private:
    double radijus; 
    static int br;
public:
    Krug() {
        radijus = 0.0;
        br++;
    }
    static int brojDeklariranih() {
        return br;
    }
};

int Krug::br = 0;

int main() {
    Krug k;
    cout << "Broj deklariranih objekata klase Krug: " << Krug::brojDeklariranih() << endl;

    Krug k1;
    cout << "Broj deklariranih objekata klase Krug: " << Krug::brojDeklariranih() << endl;

    Krug K[3];
    cout << "Broj deklariranih objekata klase Krug: " << Krug::brojDeklariranih() << endl;

    return 0;
}
```

**Ispis programa:**

- Nakon deklaracije objekta `k` klase `Krug`:
  ```
  Broj deklariranih objekata klase Krug: 1
  ```

- Nakon deklaracije objekta `k1` klase `Krug`:
  ```
  Broj deklariranih objekata klase Krug: 2
  ```

- Nakon deklaracije niza `K` od tri objekta klase `Krug`:
  ```
  Broj deklariranih objekata klase Krug: 3
  ```

**Napomena:** Na kraju programa destruktor se poziva za svaki objekt klase `Krug`, smanjujući broj deklariranih objekata.

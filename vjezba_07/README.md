# Vježba 7 - Tokovi i datoteke

## 1. Uvod u tokove i datoteke

U C++, tokovi se koriste za komunikaciju između programa i uređaja, kao i za manipulaciju podacima. Datoteke su organizirane strukture podataka koje pohranjuju informacije na vanjskom uređaju.

---

## 2. Osnovne operacije s datotekama

### 2.1 Pisanje u datoteku

```cpp
#include <fstream>
using namespace std;

int main() {
    // Deklaracija objekta izlaznog toka (ofstream) i otvaranje datoteke za pisanje
    ofstream out_file("example.txt");

    // Provjera uspješnosti otvaranja datoteke
    if (!out_file) {
        cerr << "Nemoguće otvoriti datoteku." << endl;
        return 1;
    }

    // Pisanje podataka u datoteku
    out_file << "Hello, World!" << endl;
    out_file << 42 << " " << 3.14;

    // Zatvaranje datoteke
    out_file.close();

    return 0;
}
```

### 2.2 Čitanje iz datoteke

```cpp
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main() {
    // Deklaracija objekta ulaznog toka (ifstream) i otvaranje datoteke za čitanje
    ifstream in_file("example.txt");

    // Provjera uspješnosti otvaranja datoteke
    if (!in_file) {
        cerr << "Nemoguće otvoriti datoteku." << endl;
        return 1;
    }

    // Čitanje podataka iz datoteke
    string line;
    while (getline(in_file, line)) {
        cout << line << endl;
    }

    // Zatvaranje datoteke
    in_file.close();

    return 0;
}
```

---

## 3. Rad s više datoteka

```cpp
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main() {
    // Otvaranje datoteke za čitanje
    ifstream in_file("cities");

    // Provjera uspješnosti otvaranja datoteke
    if (!in_file) {
        cerr << "Nemoguće otvoriti datoteku." << endl;
        return 1;
    }

    // Otvaranje druge datoteke za pisanje
    ofstream filter_file("filter");

    // Čitanje i filtriranje gradova
    string city;
    while (in_file >> city) {
        if (city != "zzz") {
            // Pisanje u drugu datoteku
            filter_file << city << " ";
        }
    }

    // Zatvaranje oba toka
    in_file.close();
    filter_file.close();

    return 0;
}
```

### 3.1 Rad s binarnim datotekama

Rad s binarnim datotekama ključan je aspekt programiranja i rukovanja podacima. Binarne datoteke često se koriste za pohranu podataka u obliku koji je učinkovitiji i kompaktniji od tekstualnih datoteka. 

#### 3.1.1 Uvod u binarne datoteke

Binarne datoteke sadrže podatke u neposrednom binarnom obliku, za razliku od tekstualnih datoteka koje koriste čitljive znakove. Prednosti binarnih datoteka uključuju manji prostor na disku i brži pristup podacima.

#### 3.1.2 Otvaranje i zatvaranje binarnih datoteka

Da biste radili s binarnim datotekama u C++, koristite `fstream` objekt. Evo primjera otvaranja binarne datoteke za pisanje:

```cpp
#include <iostream>
#include <fstream>

int main() {
    std::ofstream binaryFile("example.bin", std::ios::binary);
    // Rad s binarnom datotekom...
    binaryFile.close(); // Zatvaranje datoteke
    return 0;
}
```

#### 3.1.3 Pisanje u binarnu datoteku

Za pisanje podataka u binarnu datoteku koristite `write` metodu. U sljedećem primjeru, zapisujemo niz integera u binarnu datoteku:

```cpp
#include <iostream>
#include <fstream>

int main() {
    std::ofstream binaryFile("example.bin", std::ios::binary);

    int data[] = {42, 17, 99};
    binaryFile.write(reinterpret_cast<char*>(data), sizeof(data));

    binaryFile.close();
    return 0;
}
```

#### 3.1.4 Čitanje iz binarne datoteke

Za čitanje podataka iz binarne datoteke koristite `read` metodu. U sljedećem primjeru čitamo niz integera iz binarne datoteke:

```cpp
#include <iostream>
#include <fstream>

int main() {
    std::ifstream binaryFile("example.bin", std::ios::binary);

    int data[3];
    binaryFile.read(reinterpret_cast<char*>(data), sizeof(data));

    // Rad s učitanim podacima...

    binaryFile.close();
    return 0;
}
```


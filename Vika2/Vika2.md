# Deila og Drottna Reiknirit (Divide and Conquer Algorithms)

## Skilgreining

**Divide and conquer** er aðferðafræði þar sem stór vandamál eru brotin niður í smærri undirverkefni sem síðan eru leyst og sameinuð til að fá heildarlausn. Helstu skref eru:

1. **Deila (Divide)**: 
    - Skipta verkefni í smærri undirverkefni.
    - Undirverkefni verða að vera af sama toga.
    - Oftast skipt í 2-3 hluta.

2. **Drottna (Conquer)**:
    - Leysa undirverkefni á endurkvæman hátt.
    - Grunntilfelli eru leyst beint.

3. **Sameina (Combine)**:
    - Sameina lausnir undirverkefna og byggja heildarlausn.

---

## Rakningarvensl fyrir Deila og Drottna Reiknirit

Rakningarvensl lýsa tímaflækju slíkra reiknirita:

T(n) = aT(n/b) + f(n)

- **a**: Fjöldi undirverkefna.
- **n/b**: Stærð hvers undirverkefnis.
- **f(n)**: Kostnaður við að deila og sameina.

### Dæmi:
- Tvískipt: T(n) = 2T(n/2) + f(n)
- Þrískipt: T(n) = 3T(n/3) + f(n)
- Ójafn skipting: T(n) = T(2n/3) + T(n/3) + f(n)

**Visual dæmi:** Glæra 21 í fyrirlestrinum sýnir dæmi um tvískiptingu með endurkvæmnistré.

---

## Master Theorem

Master Theorem einfalda lausn á rakningarvenslum fyrir deila og drottna reiknirit með eftirfarandi skilyrðum:

T(n) = aT(n/b) + f(n)

- **Ef:**
    - f(n) = O(n^(log_b(a) - ε)) (með ε > 0) þá T(n) = Θ(n^(log_b(a))).
    - f(n) = Θ(n^(log_b(a))) þá T(n) = Θ(n^(log_b(a)) * log(n)).
    - f(n) = Ω(n^(log_b(a) + ε)) (með ε > 0) þá T(n) = Θ(f(n)).

**Dæmi um greiningu:**
- T(n) = 9T(n/3) + n
    - a = 9, b = 3, f(n) = n.
    - n^(log_3(9)) = n^2.
    - Hér gildir tilfelli 1 því f(n) = O(n^(2-1)).
    - **Tímaflækja:** T(n) = Θ(n^2).

---

##  Algeng Deila og Drottna Reiknirit

### 1. Helmingunarleit (Binary Search)
- **Hugmynd:** Leita í röðuðu fylki með því að útiloka helming staka í hverri ítrun.
- **Tímaflækja:** O(log n).
- **Endurkvæm útfærsla:**
```python
binary_search(arr, lo, hi, key):
    if hi < lo:
        return -1
    mid = (lo + hi) // 2
    if arr[mid] == key:
        return mid
    elif arr[mid] < key:
        return binary_search(arr, mid + 1, hi, key)
    else:
        return binary_search(arr, lo, mid - 1)
```

### 2. Veldishafning (Exponentiation by Squaring)
- **Hugmynd:** Nota an = (a^(n/2))^2 ef n er slétt, og an = a * (a^(n/2))^2 ef n er oddatala.
- **Tímaflækja:** O(log n).

### 3. Flétturöðun (Merge Sort)
- **Hugmynd:**
    - Skipta fylki í tvo helminga.
    - Raða hvorn helming endurkvæmt.
    - Sameina (flétta) undirfylki saman.
- **Tímaflækja:** O(n log n).

### 4. Karatsuba Margföldun
- **Hugmynd:** Nota færri margfaldanir með því að reikna (a+b)(c+d) - ac - bd = ad + bc.
- **Tímaflækja:** O(n^(log_2(3))) ≈ O(n^1.585).

---

## Hagnýt Dæmi

- **Póstflokkun:** Bréf eru flokkuð endurkvæmt eftir landsvæðum og svæðum þar til þau ná tilteknu útburðarsvæði.
- **Radix Röðun:** Undanfari nútíma bucket röðunar.
- **Dæmi úr tölvunarfræði:**
    - Uppflettitöflur.
    - Röðun gagna.
    - Nálgun á hagnýtum verkefnum eins og optimal substring search.

---

## Aðferðir til Að Nota

- Teikna endurkvæmnistré til að fá yfirsýn yfir keyrsluferli.
- Nota Master Theorem þar sem það á við.
- Greina skiptikostnað og sameiningarkostnað sérstaklega fyrir sértæk verkefni.

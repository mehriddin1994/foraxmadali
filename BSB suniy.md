# Bob summativ baholash — Nazorat ishi

**Fan:** MYP Dizayn (Raqamli dizayn)
**Bob:** Python’da ma’lumotlar tahlili: NumPy va Pandas
**Mezon:** A — Tadqiq qilish va tahlil qilish (Inquiring and Analysing)
**Maksimal ball:** 8

## Ko‘rsatmalar

1. Barcha topshiriqlarni bajaring. Javoblarni to‘liq jumlalar bilan yozing.
2. Kodning natijasini so‘ralgan joyda kompyutersiz, o‘ylab topishingiz kerak.
3. Javoblaringizni **jadvaldagi ma’lumotlar va kod natijalari** bilan asoslang — dalilsiz fikr past baholanadi.
4. Har bir bo‘lim qaysi mezon yo‘nalishiga (strand) tegishli ekani ko‘rsatilgan.

| Bo‘lim   | Mezon yo‘nalishi                                         | Tavsiya etilgan vaqt |
| -------- | -------------------------------------------------------- | -------------------- |
| 1-bo‘lim | A(i) Muammoni tushuntirish va yechim zaruratini asoslash | 20 daqiqa            |
| 2-bo‘lim | A(ii) Tadqiqotni aniqlash va ustuvorlashtirish           | 15 daqiqa            |
| 3-bo‘lim | A(iii) Mavjud yechimlarni tahlil qilish                  | 25 daqiqa            |
| 4-bo‘lim | A(iv) Batafsil dizayn brifini ishlab chiqish             | 20 daqiqa            |

---

## Vaziyat (kontekst)

Maktab oshxonasi mudirasi har kuni ko‘p ovqat ortib qolib, isrof bo‘layotganidan xavotirda. U sizdan **Python (NumPy va Pandas) yordamida ma’lumotlarni tahlil qiluvchi dastur** yaratishni so‘radi. Dastur qaysi taom qachon ko‘proq isrof bo‘lishini ko‘rsatib, oshxonaga qancha porsiya tayyorlash bo‘yicha qaror qabul qilishda yordam berishi kerak.

Mudira bir haftalik ma’lumotlarni `oshxona.csv` faylida berdi:

| kun        | taom    | tayyorlangan | sotilgan | narx (so‘m) |
| ---------- | ------- | ------------ | -------- | ----------- |
| Dushanba   | Osh     | 120          | 110      | 18000       |
| Dushanba   | Lag‘mon | 80           | 60       | 15000       |
| Dushanba   | Somsa   | 150          | 140      | 5000        |
| Seshanba   | Osh     | 120          | 95       | 18000       |
| Seshanba   | Lag‘mon | 80           | 72       | 15000       |
| Seshanba   | Somsa   | 150          | 120      | 5000        |
| Chorshanba | Osh     | 120          | 118      | 18000       |
| Chorshanba | Lag‘mon | 80           | 55       | 15000       |
| Chorshanba | Somsa   | 150          | 148      | 5000        |
| Payshanba  | Osh     | 120          | 90       | 18000       |
| Payshanba  | Lag‘mon | 80           | 78       | 15000       |
| Payshanba  | Somsa   | 150          | 100      | 5000        |

---

## 1-bo‘lim. Muammoni tushuntirish va asoslash — A(i)

Quyidagi kod ishga tushirildi:

```python
import pandas as pd
import numpy as np

df = pd.read_csv("oshxona.csv")
df["isrof"] = df["tayyorlangan"] - df["sotilgan"]
df["isrof_summa"] = df["isrof"] * df["narx"]

print(df.groupby("taom")["isrof"].sum())
print(df.groupby("kun")["isrof"].sum())
print(df["isrof_summa"].sum())
print(round(df["isrof"].sum() / df["tayyorlangan"].sum() * 100, 2))
```

Natija:

```
taom
Lag'mon     55
Osh         67
Somsa       92
Name: isrof, dtype: int64

kun
Chorshanba    29
Dushanba      40
Payshanba     82
Seshanba      63
Name: isrof, dtype: int64

2491000

15.29
```

**1.1.** `df["isrof"] = df["tayyorlangan"] - df["sotilgan"]` qatori nima ish bajaradi? Nima uchun bu yerda `for` siklidan foydalanish shart emas? _(2–3 jumla)_

**1.2.** Natijalar asosida oshxonadagi muammoni **kamida uchta aniq raqam** keltirgan holda tushuntiring.

**1.3.** Somsa eng ko‘p porsiyada isrof bo‘lgan (92 ta), lekin pul jihatidan eng katta zarar qaysi taomga to‘g‘ri keladi? Hisoblab ko‘rsating va bu farq nima uchun muhimligini izohlang.

**1.4.** Nima uchun bu muammoni qo‘lda (daftarda hisoblab) emas, balki dastur yordamida hal qilish kerak? Kamida **ikkita sabab** bilan asoslang. Bu dasturdan kimlar foyda ko‘radi?

---

## 2-bo‘lim. Tadqiqotni aniqlash va ustuvorlashtirish — A(ii)

**2.1.** Yechim yaratish uchun javob topilishi kerak bo‘lgan **kamida 5 ta tadqiqot savoli** yozing. Har bir savol uchun quyidagi jadvalni to‘ldiring:

| №   | Tadqiqot savoli | Ma’lumot manbasi (birlamchi / ikkilamchi) | Qanday topiladi (so‘rovnoma, intervyu, kod, internet…) | Ustuvorlik (1 — eng muhim) |
| --- | --------------- | ----------------------------------------- | ------------------------------------------------------ | -------------------------- |
| 1   |                 |                                           |                                                        |                            |
| 2   |                 |                                           |                                                        |                            |
| 3   |                 |                                           |                                                        |                            |
| 4   |                 |                                           |                                                        |                            |
| 5   |                 |                                           |                                                        |                            |

**2.2.** Eng muhim deb belgilagan **ikkita** savolingiz nima uchun birinchi o‘rinda turishini tushuntiring.

**2.3.** Quyidagi tadqiqot savollariga javob berish uchun qaysi Pandas yoki NumPy funksiyasidan foydalanasiz? Kod qatorini yozing.

| Savol                                                            | Kod |
| ---------------------------------------------------------------- | --- |
| a) Faqat Payshanba kungi ma’lumotlarni qanday ajratib olaman?    |     |
| b) Har bir taom bo‘yicha o‘rtacha sotuv qancha?                  |     |
| c) Isrofi 20 tadan ko‘p bo‘lgan qatorlar qaysilar?               |     |
| d) Jadvalni isrof bo‘yicha kamayish tartibida qanday saralayman? |     |

**2.4.** Hozirgi ma’lumotlar to‘plamida (bir hafta, 12 qator) qanday **cheklovlar** bor? Ishonchli xulosa chiqarish uchun yana qanday ma’lumotlar to‘plash kerak? _(kamida 2 ta)_

---

## 3-bo‘lim. Mavjud yechimlarni tahlil qilish — A(iii)

### 3A. Kodni o‘qish va natijani bashorat qilish

**3.1.** Quyidagi kodning natijasini yozing:

```python
somsa_sotuv = np.array([140, 120, 148, 100])
print(somsa_sotuv.mean())
print(somsa_sotuv.max() - somsa_sotuv.min())
```

**3.2.** Quyidagi kodning natijasini yozing va u oshxona mudirasiga qanday foyda berishini izohlang:

```python
somsa_isrof = np.array([10, 30, 2, 50])
print(np.where(somsa_isrof > 20, "yuqori", "past"))
```

**3.3.** Somsa sotuvining standart chetlanishi `somsa_sotuv.std()` ≈ **18.63**, Osh sotuvining standart chetlanishi esa ≈ **11.6**. Bu raqamlar nimani bildiradi? Qaysi taomga tayyorlanadigan porsiya sonini rejalashtirish qiyinroq va nima uchun?

### 3B. Uch xil yechimni solishtirish

Uchta o‘quvchi har bir taom bo‘yicha jami isrofni hisoblash uchun turli kod yozdi:

**A yechim — oddiy Python:**

```python
taomlar = ["Osh", "Lag'mon", "Somsa"] * 4
tayyor  = [120, 80, 150] * 4
sotilgan = [110, 60, 140, 95, 72, 120, 118, 55, 148, 90, 78, 100]
natija = {}
for i in range(len(taomlar)):
    t = taomlar[i]
    natija[t] = natija.get(t, 0) + tayyor[i] - sotilgan[i]
print(natija)
```

**B yechim — NumPy:**

```python
tayyor = np.array([120, 80, 150] * 4).reshape(4, 3)
sotilgan = np.array([110, 60, 140, 95, 72, 120,
                     118, 55, 148, 90, 78, 100]).reshape(4, 3)
print((tayyor - sotilgan).sum(axis=0))
```

**C yechim — Pandas:**

```python
df = pd.read_csv("oshxona.csv")
df["isrof"] = df["tayyorlangan"] - df["sotilgan"]
print(df.groupby("taom")["isrof"].sum())
```

**3.4.** B yechimda `reshape(4, 3)` va `sum(axis=0)` nima vazifani bajaradi? Natija qanday ko‘rinishda chiqadi?

**3.5.** Uchala yechimni quyidagi mezonlar bo‘yicha solishtiring va jadvalni to‘ldiring:

| Mezon                                                     | A (Python) | B (NumPy) | C (Pandas) |
| --------------------------------------------------------- | ---------- | --------- | ---------- |
| Kodni o‘qish va tushunish osonligi                        |            |           |            |
| Katta hajmdagi ma’lumot (masalan, 1 yillik) bilan ishlash |            |           |            |
| Ma’lumot fayldan (CSV) o‘qilishi                          |            |           |            |
| Natijaning tushunarliligi (ustun nomlari, belgilar)       |            |           |            |
| Yangi taom qo‘shilganda o‘zgartirish osonligi             |            |           |            |

**3.6.** Qaysi yechim oshxona uchun eng mos? Javobingizni yuqoridagi jadval asosida asoslang va tanlagan yechimingizning **bitta kamchiligini** ham ko‘rsating. Bu tahlildan o‘z dasturingiz uchun nimalarni o‘rgandingiz?

---

## 4-bo‘lim. Dizayn brifi — A(iv)

**4.1.** Yuqoridagi tahlillar asosida oshxona uchun yaratiladigan dasturning **batafsil dizayn brifini** yozing. Brifda quyidagilar bo‘lishi shart:

- **Muammo bayoni** (1–2 jumla, raqamlar bilan)
- **Maqsad** — dastur nimaga erishishi kerak
- **Maqsadli foydalanuvchi(lar)** va ularning ehtiyojlari
- **Dastur bajaradigan asosiy funksiyalar** (kamida 4 ta, har biri uchun ishlatiladigan Pandas/NumPy vositasi)
- **Kirish va chiqish ma’lumotlari** (qaysi fayl, qaysi ustunlar; natija qanday ko‘rsatiladi)
- **Cheklovlar** (vaqt, texnik bilim, ma’lumot hajmi va h.k.)
- **Muvaffaqiyat qanday o‘lchanadi** (masalan, isrof foizi qanchaga kamayishi kerak)

**4.2.** Tadqiqotingiz va mavjud yechimlar tahlili brifingizdagi qaysi qarorlarga **bevosita ta’sir qilganini** ikkita misol bilan ko‘rsating.

---

## Baholash mezoni (Mezon A, maksimal 8)

| Ball    | Daraja tavsifi                                                                                                                                                                                                                                                                                                                          | Ushbu nazorat ishi uchun aniqlashtirish                                                                                                                                                                                                                                                                                                               |
| ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **0**   | Quyidagi tavsiflarning hech biriga javob bermaydi.                                                                                                                                                                                                                                                                                      | —                                                                                                                                                                                                                                                                                                                                                     |
| **1–2** | O‘quvchi: (i) yechim zaruratini **bayon qiladi**; (ii) ba’zi tadqiqot yo‘nalishlarini **aniqlaydi**; (iii) mavjud yechimlardan birini **sanab o‘tadi**; (iv) dizayn brifining ba’zi elementlarini **sanab o‘tadi**.                                                                                                                     | Muammo umumiy so‘zlar bilan aytilgan, raqamlar yo‘q. 1–2 ta savol yozilgan. Kod natijalari noto‘g‘ri yoki yo‘q. Brif bir-ikki jumladan iborat.                                                                                                                                                                                                        |
| **3–4** | O‘quvchi: (i) yechim zaruratini **qisqacha tushuntiradi**; (ii) tadqiqotni **aniqlaydi va ba’zilarini** ustuvorlashtiradi; (iii) bir qator mavjud yechimlarni **ta’riflaydi**; (iv) asosiy tadqiqot topilmalarini aks ettiruvchi **asosiy brifni** yozadi.                                                                              | Muammo 1–2 ta raqam bilan tushuntirilgan. 3–4 ta savol, ustuvorlik asoslanmagan. Kod natijalarining ko‘pchiligi to‘g‘ri, solishtirish yuzaki. Brifda 3–4 ta element bor.                                                                                                                                                                              |
| **5–6** | O‘quvchi: (i) yechim zaruratini **tushuntiradi**; (ii) tadqiqotni **aniqlaydi va ustuvorlashtiradi** (asosan mustaqil); (iii) bir qator mavjud yechimlarni **tahlil qiladi**; (iv) tegishli tadqiqot topilmalarini **tahlil qilib**, dizayn brifini **ishlab chiqadi**.                                                                 | Muammo ≥3 raqam bilan, foydalanuvchi ko‘rsatilgan. 5 ta savol, manba va ustuvorlik bilan. Kod natijalari to‘g‘ri, jadval to‘ldirilgan, tanlov asoslangan. Brifning barcha qismlari bor, lekin tahlilga bog‘lanishi kuchsiz.                                                                                                                           |
| **7–8** | O‘quvchi: (i) yechim zaruratini **batafsil tushuntiradi va asoslaydi**; (ii) muammoni hal qilish uchun **asosiy tadqiqotni** mustaqil aniqlaydi va ustuvorlashtiradi; (iii) bir qator mavjud yechimlarni **batafsil tahlil qiladi**; (iv) tegishli tadqiqot topilmalarini **tahlil qilib**, **batafsil dizayn brifini** ishlab chiqadi. | Porsiya va pul zarari farqi (1.3) chuqur izohlangan, ≥2 sabab bilan asoslangan. Savollar aniq, ustuvorlik mantiqiy asoslangan, cheklovlar ko‘rsatilgan. Barcha kod natijalari to‘g‘ri; uch yechim kuchli/kuchsiz tomonlari bilan tahlil qilingan. Brif to‘liq, o‘lchanadigan muvaffaqiyat ko‘rsatkichi bor va har bir qaror tahlilga aniq bog‘langan. |

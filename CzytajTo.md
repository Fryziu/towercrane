# Mod Tower Crane (Żuraw Wieżowy)

Aby ułatwić wznoszenie budynków, żuraw wyznacza obszar budowy, wewnątrz którego gracz otrzymuje uprawnienia do latania.

Przeglądaj na: [GitHub](https://github.com/Fryziu/towercrane)


Dźwig jest montowany w całości poprzez postawienie wyłącznie bloku bazy.  
Wymiary dźwigu (które wyznaczają obszar budowy) oraz długość liny można konfigurować w grze.

![Tower Crane](https://github.com/minetest-mods/towercrane/blob/master/towercrane640.png)


## Wprowadzenie i obsługa

* **Wytwarzanie (Crafting):**  
  Stwórz blok bazy dźwigu, używając 5 sztabek żelaza/stali (wypełnij nimi cały górny rząd oraz lewą kolumnę) oraz żółtego barwnika umieszczonego w dolnym środkowym slocie stołu rzemieślniczego. Wymagane materiały mogą się różnić w zależności od gry (np. w VoxeLibre używane jest żelazo `mcl_core:iron_ingot` i żółty barwnik `mcl_dyes:yellow`).

* **Stawianie bazy:**  
  Postaw blok bazy żurawia. Ramię dźwigu zostanie w późniejszym kroku skierowane dokładnie w tę stronę, w którą patrzy gracz podczas stawiania bazy.

* **Budowa konstrukcji:**  
  Kliknij prawym przyciskiem myszy (PPM) na blok bazy i ustaw wymiary: wysokość oraz szerokość ramienia (domyślnie od 8 do 32 bloków). Dźwig rozstawi się automatycznie zgodnie z tymi ustawieniami.  
  *Uwaga:* Jeśli na drodze masztu/ramienia nie ma wystarczająco dużo wolnej przestrzeni lub obszar budowy nachodzi na teren chroniony innego gracza, dźwig nie zostanie wzniesiony.

* **Uruchamianie dźwigu:**  
  Kliknij prawym przyciskiem myszy na przełącznik na dole masztu, aby włączyć dźwig (przycisk zmieni kolor na zielony i otrzymasz uprawnienie do latania). Postać zostanie ustawiona przed maszyną. Aby wzbić się w powietrze, włącz tryb latania klawiszem **K**, a następnie wznosź się **Spacją**.

* **Wyłączanie dźwigu:**  
  Kliknij ponownie przełącznik PPM, aby zatrzymać dźwig i opuścić strefę budowy. Postać zostanie bezpiecznie sprowadzona na ziemię przed maszt, a uprawnienie do latania zostanie odebrane.

* **Demontaż:**  
  Aby całkowicie zdemontować konstrukcję dźwigu, po prostu zniszcz blok bazy.


## Wymagania i zależności

**Wymagany jest silnik Minetest / Luanti w wersji 5.0 lub nowszej!**

* `xcompat` – Zapewnia kompatybilność receptur i dźwięków pomiędzy różnymi grami. (Ostatnia wersja moda bez zależności `xcompat` to wydanie `2024-04-26`).


# Licencja

Copyright (C) 2017-2020 Joachim Stolberg  
Kod: Na licencji GNU LGPL w wersji 2.1 lub nowszej. Zobacz LICENSE.txt oraz http://www.gnu.org/licenses/lgpl-2.1.txt  
Tekstury: W większości CC0 (autor: Ammoth)

* `morelights_extras_blocklight.png`: CC BY-SA 4.0 (autor: random-geek)


# History:

* 2017-06-04  v0.01  first version
* 2017-06-06  v0.02  Hook bugfix
* 2017-06-07  v0.03  fixed 2 bugs, added config.lua and sound
* 2017-06-08  v0.04  recipe and rope length now configurable
* 2017-06-10  v0.05  resizing bugfix, area protection added
* 2017-07-11  v0.06  fixed the space check bug, settingtypes added
* 2017-07-16  v0.07  crane remove bug fix
* 2017-07-16  v0.08  player times out bugfix
* 2017-08-19  v0.09  crane protection area to prevent crane clusters
* 2017-08-27  v0.10  hook instance and sound switch off bug fixes
* 2017-09-09  v0.11  further player bugfixes
* 2017-09-24  v0.12  Switched from entity hook model to real fly privs
* 2017-10-17  v0.13  Area protection bugfix
* 2017-11-01  v0.14  Crane handing over bugfix
* 2017-11-07  v0.15  Working zone is now restricted to areas with necessary rights
* 2018-02-27  v0.16  "fly privs" bug fixed (issue #2)
* 2018-04-12  v0.17  "area owner changed" bug fixed (issue #3)
* 2018-05-28  v1.0 Mod released
* 2019-09-08  v2.0 Completely restructured, protection areas removed
* 2019-12-03  v2.1 Bugfix issue #2 (Some players still have "fly" after detaching)
* 2020-01-03  V2.2 dying player bugfix (when fly mode is disabled)
* 2020-03-16  V2.3 switched to 16 bit textures (by tuedel/Ammoth) and crane upright time increased to 5 real days
* Further updates: https://github.com/minetest-mods/towercrane/commits/master/
* //Fryziu
* 2026-10-24 Gemini 3.8 Flash

## Poprawki kompatybilności dla Luanti 5.x i VoxeLibre (Wykaz zmian)

Ten fork wprowadza szereg usprawnień, poprawek błędów oraz pełną zgodność z grą **VoxeLibre** (MineClone2) i nowoczesnymi wersjami silnika **Luanti (Minetest 5.8+)**.

### 1. Integracja z VoxeLibre / MineClone
* **Obsługa receptur i Księgi Rzemiosła:** Dodano bezpośrednie wsparcie dla `mcl_core:iron_ingot` i `mcl_dyes:yellow` oraz grupy `group:dye_yellow`. Receptury rejestrowane są w fazie ładowania, dzięki czemu od razu pojawiają się w Księdze Receptur (`mcl_craftguide`).
* **Naprawa upuszczania bloku przy kopaniu ręką:** Dodano grupy `handy = 1`, `pickaxey = 2` i `material_metal = 1` oraz jawny parametr `drop`. Zniszczenie bazy pustą ręką nie powoduje już utraty przedmiotu.
* **Odporność na wybuchy i przypadkowe wykopanie:** Maszt, ramię i przeciwwaga są teraz odporne na eksplozje (`on_blast`) i bezpośrednie wykopywanie, co zapobiega rozpadaniu się konstrukcji dźwigu.

### 2. Modernizacja dla silnika Luanti 5.x
* **Usunięcie błędu `drawtype`:** Poprawiono błędny parametr `drawtype = "node"` na `"normal"`, likwidując ostrzeżenia w konsoli i błędy renderowania przełącznika.
* **Nowoczesny interfejs (Formspec):** Przebudowano formularz do standardu `formspec_version[4]`, eliminując nachodzenie na siebie pola tekstowego i przycisku.
* **Poprawna konfiguracja:** Zastosowano `minetest.settings:get_bool` w `config.lua`.
* **Kolejność ładowania:** W `mod.conf` dodano zależności opcjonalne (`optional_depends`), gwarantujące prawidłową kolejność inicjalizacji.

### 3. Stabilność i wydajność
* **Ochrona przed crashami serwera:** Zabezpieczono funkcję `get_my_crane_pos` przed błędem `nil value`.
* **Ochrona przed przypadkowym zniszczeniem:** Zamknięcie okna klawiszem ESC nie usuwa już istniejącego dźwigu.
* **Wygodne wpisywanie wymiarów:** Parser wymiarów akceptuje spacje, przecinki oraz znak 'x' (np. `12,12`, `12, 12`, `16x16`).
* **Optymalizacja I/O (Baza SQLite / Docker):** Zastąpiono ciągły zapis do bazy SQLite co 1 sekundę pamięcią podręczną RAM, co radykalnie zmniejsza obciążenie dysku w kontenerach Docker.
* **Bezpieczne logowanie:** Odblokowywanie fizyki gracza przy wejściu na serwer, co zapobiega zablokowaniu postaci po awarii lub rozłączeniu.

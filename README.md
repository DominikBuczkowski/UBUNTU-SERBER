## Ogólny test komputera
### 1. Pamięć RAM
- `free` wolna pamięć, `free -m` w MB, `free -h` w GB
-  "Menedżer urządzeń" `lshw -short` zapis urządzeń w PC, `lshw -c memory` Zajęte banki, taktowanie, typ, wielkość kości, model,


### 2. Dyski 
- `hdparm -i !ścieżka do dysku!` pokazuje *Model*               Patrz dysk twardy test1
- `hdparm -i !ścieżka do dysku!` pokazuje *Numer seryjny*       Patrz dysk twardy test1

- `lshw -c disk` pokazuje *Numer seryjny*
- 
> ścieżkę można sprawdzić przez `df`
- `fdisk -l`LUB `df -h`  sprawdza ilość wolnego miejsca na dysk
- Procent zajętego dysku `df -h`, wartość *use%*
- `df -Th` sprawdza system pliku
> XDXDXDXDSDXDX JAK SIĘ KURWA SCROLLUJE


### 3. Procesor
- `sudo cat /proc/cpuinfo` Wyświetla informacje o: zegarach, nazwie, modelu, liczbie rdzeni, pamięci CACHE, taktowanie


### 4. Karta graficzna
- `lshw -c display` wyświetla informacje o: producencie (*vendor*), zegarach, szerokości busa, modelu, generacji (zaraz po dwukropku w *product*)


### 5. Karta sieciowa
- `lshw -c network` wyświetla informacje o: nr seryjnym, prodcencie, modelu, wersji, adres MAC (*serial*)

### 6. INNE
- maska plików `umask`
- aktualny użytkownik `whoami`
- oznaczenie terminala użytkownika `who` *2 WARTOŚĆ KTÓRA SIĘ WYŚWIETLI*
- długość czasu pracy komputera `uptime`

### 7. Płyta główna
- `sudo dmidecode -t 2` numer seryjnyh i producent
- 
***

# Ubuntu Server – przygotowanie do egzaminu
1.	Zaloguj się do systemu – login to administrator, hasło to Teb2022+  `nazwa użytkownika potem hasło`

2.	Utwórz kilka widoków konsoli tak aby móc przełączać się między widokami i zaloguj się w każdej z nich `ALT + (F1 - F6)`

3.	Wyświetl w jednej konsoli instrukcje na temat netplan `man netplan`

4.	Znajdź w instrukcji przykład konfiguracji adresów karty sieciowej `line 941` ???

5.	Wyświetl ustawienia kart sieciowych `ifconfig -a` / `ip addr show`
6.	Wyświetl nazwy połączeń sieciowych 
7.	Wyświetl plik konfiguracyjny interfejsu sieciowego `cd etc/netplan/00-installer-config.yaml` , otworzenie - `nano 00-install-config.yaml`
8.	Utwórz kopię zapasową pliku konfiguracyjnego interfejsów sieciowych `sudo cp nano 00-install-config.yaml 00-install-config.yaml.old`
9.	Na drugiej karcie sieciowej ustaw ip 10.10.10.124 o masce 255.255.255.0 i bramie domyślnej 10.10.10.3, nazwa połączenia „egzamin”
10.	Przetestuj konfigurację połączeń sieciowych `sudo netplan try`
11.	Zaakceptuj konfigurację połączenie sieciowych `sudo netplan apply`
12.	Uruchom ponownie system `sudo reboot`
13.	Wyświetl ustawienia połączeń sieciowych `ifconfig`
14.	Przywróć ustawienia karty sieciowej do pierwotnej – skopiuj plik zapasowy i przetestuj działanie netplan `sudo cp etc/netplan/ 00-installer-config.yaml.old 00-installer-config.yaml` `sudo netplan try`
15.	Uruchom ponownie system `sudo reboot`
16.	Podłącz dysk USB do komputera (w przypadku wirtualnej maszyny wybierz „connect to virtual machine” lub z menu Player wybierz dysk i naciśnij Connect – na egzaminie nie będzie trzeba tego robić)
17.	Wyświetl dyski dostępne w systemie i wskaż dysk USB `sudo fdisk -l`
18.	Podaj jaki system plików jest w przygotowany w dysku USB `FAT32`
19.	Co należy zrobić aby korzystać z dysku USB? `niewiem `
20.	Zamontuj dysk USB w folderze /media/dyskUSB
21.	Wyświetl listę plików z dysku USB
22.	Przekieruj dane z pliku zawierającego użytkowników do pliku użytkownicy.txt na dysku USB
23.	Wyświetl listę plików dysku USB i zawartość pliku użytkownicy.txt
24.	Odmontuj dysk USB
25.	Utwórz konto egzamin
26.	Utwórz grupę klasy
27.	Dodaj konto egzamin do grupy użytkowników klasy
28.	Wyświetl plik zawierający użytkowników
29.	Wyświetl plik zawierający grupy
30.	Zablokuj użytkownika egzamin
31.	Odblokuj użytkownika egzamin
32.	Ustaw aby użytkownik egzamin musiał zmienić hasło podczas logowania
33.	Zmień hasło użytkownika egzamin na ZAQ!wsx
34.	Utwórz folder o nazwie Zadania w folderze użytkownika egzamin
35.	Wykonaj archiwum, pliku konfiguracji interfejsów sieciowych serwera o nazwie kopia.tar i umieść je w folderze Zadania
36.	Wykonaj test połączenia z adresem onet.pl
37.	Wykonaj test połączenia z adresem 10.10.10.3
38.	Zainstaluj usługę DHCP na serwerze
39.	Określ zakres adresów usługi DHCP na 10.10.10.30 – 10.10.10.40
40.	Zarezerwuj adres 10.10.10.29 dla adresu twojego komputera
41.	Zainstaluj na serwerze usługę FTP
42.	Serwer FTP ma działać tylko dla użytkowników anonimowych
43.	Komunikat powitalny serwera FTP to „Witaj na egzaminie!”
44.	Utwórz katalog pub w lokalizacji /srv/ftp
45.	Skonfiguruj możliwość zapisu do katalogu pub dla użytkowników anonimowych
46.	przetestuj działanie serwera FTP na lokalnym serwerze
47.	Zainstaluj serwer  HTTP na serwerze
48.	Utwórz katalog /www
49.	Ustal prawa do powyższego katalogu /www na 555
50.	odczytaj użytkownika i grupę na prawach których działa serwer http
51.	ustaw właściciela i grupę na prawach których działa serwer HTTTP dla katalogu /www
52.	w katalogu /www utwórz plik index.html o dowolnej treści
53.	ustal prawa 444 do pliku index.html dla użytkownika i grupy na których działa serwer http
54.	w serwerze http zmień port na którym działa serwer http na 8080
55.	w serwerze http zmień lokalizację głównej witryny Web na folder /www
56.	zainstaluj na serwerze serwer DNS
57.	wyświetl pliki konfiguracyjne
58.	utwórz przykładową strefę przeszukiwania do przodu
59.	utwórz przykładową strefę przeszukiwania do tyłu

## 1. _Podstawy 
#### I.  <?php ?> - otwieranie i zamykanie skryptu php (tagi <script language="php"> są przestarzałe)
#### II.  $ - deklaracja zmiennej 
#### III. echo, print - wyswietlanie tekstu i znaczników HTML w przegladarce
#### IV.  Typy danych:
-  string - znakowy <br>
-  int - calkowite <br>
-  float/double - zmiennoprzecinkowe  <br>
-  bool - prawda/falsz <br>

#### V.   Komentowanie 
- //,
- #,
- /* ... */
#### VI.  Laczenie napisów(konkatenacja) - wykonujemy kropką


## 2. _Podstawowe operacje: operatory, instrukcje warunkowe, pętle
    I. operatory porównania i logiczne
        a. operatory porównania:
        ==      - sprawdza czy się równa (wartość)
        ===     - sprawdza czy są identyczne (wartość ORAZ typ danych)
        !=, <>  - sprawdza czy jest różne
        !==     - sprawdza czy są nieidentyczne (różna wartość LUB różny typ)
        <, >    - mniejszy, większy
        <=, >=  - mniejszy lub równy, większy lub równy
        
        b. operatory logiczne:
        && (and) - i (oba warunki muszą być prawdziwe)
        || (or)  - lub (przynajmniej jeden warunek musi być prawdziwy)
        !        - zaprzeczenie (not)

    II. instrukcje warunkowe
        a. if / elseif / else - wykonanie kodu w zależności od spełnienia warunku
        b.
            switch($zmienna) - przyjmuje zmieną którą chcemy sprawdzić 
            case wartosc - sprawdza czy zmienna jest równa danej wartości> Jeśli tak, wykonuje kod znajdujacy sie po nim.
            default - działa wtedy jak zaden case nie pasował(tak jak else)
                <?php
                $dzien = 2;

                switch ($dzien) {
                    case 1:
                        echo "Poniedziałek";
                        break;
                    case 2:
                        echo "Wtorek"; - to sie wykona bo  $dzien = 2, a case 2
                        break;
                    default:
                        echo "Inny dzień tygodnia";
                        break;
                }
                ?>

    III. pętle
        a. for - pętla o zdefiniowanej liczbie powtórzeń
                <?php
                // (definiuje zmienną; stawia warunek; dodaje po 1 do zmiennej)
                for ($i = 1; $i <= 5; $i++) {
                    echo "Liczba: $i<br>";
                }
                ?>
                // calosc bedzie sie powtarzac za $i będzie równe 5 ($i <= 5) wiec wypisze tekst 5 razy
            
        b. while - pętla wykonująca się dopóki warunek jest prawdziwy
                <?php
                $licznik = 1;

                while ($licznik <= 3) {         // warunek to zmienna=3 wykonuje sie az zmienna osiagnie 3 bo <= zamiast <
                    echo "Liczba: $licznik<br>";
                    $licznik++; // bedzie dodawac do zmiennej 1 az osiagnie 3
                }
                ?>

        c. do...while - pętla wykonująca się przynajmniej raz, a potem sprawdza warunek
                <?php
                $x = 10;

                do {
                    $x++; // wykona sie przynajmniej raz niezalznie od tego czy warunek jest prawdziwy 
                } while ($x < 5); // jak sie zgadza to cofa sie do 'do..' i wykonuje dalej 
                ?>
        d. foreach - pętla przeznaczona specjalnie do iteracji po tablicach
                <?php
                // Tablica asocjacyjna
                $uczniowie = [
                    [
                        "imie" => "Jan",
                        "nazwisko" => "Kowalski",
                        "klasa" => "4B2"
                    ],
                    [
                        "imie" => "Anna",
                        "nazwisko" => "Nowak",
                        "klasa" => "4B2"
                    ],
                    [
                        "imie" => "Piotr",
                        "nazwisko" => "Zieliński",
                        "klasa" => "4B1"
                    ]
                ];

                // Pierwsza pętla przechodzi przez każdego ucznia po kolei
                foreach ($uczniowie as $indeks => $uczen) {
                    echo "<b>Uczeń numer " . ($indeks + 1) . ":</b><br>";
                    
                    // Druga pętla przechodzi przez dane konkretnego ucznia (klucz => wartość)
                    foreach ($uczen as $klucz => $wartosc) {
                        echo "- $klucz: $wartosc<br>";
                    }
                    
                    echo "<br>"; // Dodatkowa przerwa między uczniami
                }
                ?>

## 3. _Praca z tablicami i funkcjami
    Tablice w PHP występują na egzaminie bardzo często, szczególnie przy odbieraniu danych i wynikach z bazy.
    I. Rodzaje tablic:
        a. Indeksowane numerycznie: $owoce = ["jabłko", "banan"];
        b. Asocjacyjne (klucz => wartość): $osoba = ["imie" => "Jan", "wiek" => 20];
    II. Funkcje tablicowe:
        a. count($tablica) – zliczanie elementów tablicy.
        b. 
            b. 
            sort($zmienna)  - sortuje tablicę rosnąco (liczby albo od A do Z).
            rsort($zmienna) - sortuje tablicę malejąco (liczby albo od Z do A).
            asort($zmienna) - sortuje tablicę asocjacyjną rosnąco według wartości, zachowując powiązania.
            arsort($zmienna) - sortuje tablicę asocjacyjną malejąco według wartości, zachowując powiązania.
            ksort($zmienna) - sortuje tablicę asocjacyjną rosnąco według kluczy, zachowując powiązania.
            krsort($zmienna) - sortuje tablicę asocjacyjną malejąco według kluczy, zachowując powiązania.

    III. Własne funkcje:
        a. function nazwaFunkcji($parametr) { return $wynik; } 
            ($parametr) – dane wejściowe (zmienne), które przekazujesz do wnętrza funkcji, aby mogła na nich wykonać operacje. 
            Funkcja może nie mieć żadnych parametrów (wtedy nawiasy są puste: ()) lub może ich mieć kilka po przecinku.
                <?php
                function dodaj($a, $b) {
                    $wynik = $a + $b;
                    return $wynik; // wyciaga wynik poza funkcje 
                }

                $suma = dodaj(5, 10); 

                echo $suma; // Wynik w przeglądarce: 15
                ?>
  
    IV. Dołączanie plików:
        a. include 'plik.php' / require 'plik.php' – dołączenie zewnętrznego skryptu (np. z nagłówkiem lub połączeniem do bazy).
        b. include_once / require_once – jednorazowe dołączenie pliku.
            
            require_once – Używaj do najważniejszych plików bazowych (np. plik z połączeniem do bazy danych db.php lub konfiguracja config.php).
            Jeśli plik z bazą danych nie istnieje lub ma błąd, cała strona nie ma sensu bytu – lepiej, 
            żeby skrypt natychmiast się zatrzymał, niż wyświetlał uszkodzoną treść. Dodatkowo końcówka _once chroni przed przypadkowym 
            podwójnym dołączeniem tego samego połączenia.
            
            include / include_once – Używaj do elementów strukturalnych/wizualnych (np. szablon nagłówka header.php, stopki footer.php czy menu boczne).
            Jeśli zgubi się plik stopki, strona wciąż może działać (choć będzie brzydsza), 
            więc wystarczy ostrzeżenie zamiast zatrzymywania całego serwisu.


## 4. _Formularze i zmienne superglobalne
    I. Zmienne superglobalne:
        a. $_POST['nazwa_pola'] – odbieranie danych przesłanych metodą POST (ukryte w nagłówku, zalecane dla formularzy).
            <!DOCTYPE html>
            <html lang="pl">
            <head>
                <meta charset="UTF-8">
                <title>Formularz</title>
            </head>
            <body>
                <form method="POST" action="skrypt.php">
                    <label for="login">Wpisz login:</label>
                    <input type="text" name="login" id="login">
                    <button type="submit">Wyślij</button>
                </form>
            </body>
            </html>

            <?php
           //sprawdza czy dane z 'login' zostaly przeslane 
            if (isset($_POST['login'])) {
                
                // wyciaga dane z pola tekstowego
                $odebranyLogin = $_POST['login'];
                
                // Wyświetlamy powitanie na stronie
                echo "Witaj, " . $odebranyLogin . "!";
            } else {
                echo "Brak danych do wyświetlenia.";
            }
            ?>

        b. $_GET['nazwa_pola'] – odbieranie danych przesłanych metodą GET (widoczne w adresie URL).
            np. strona.php?id=5&kategoria=ksiazki       >>>>     $idKategorii = $_GET['id'];

    II. Sprawdzanie stanu formularza:
        a. isset($zmienna) – sprawdzenie, czy zmienna istnieje 
        b. empty($zmienna) – sprawdzenie, czy pole formularza jest puste.

    III. Funkcje pomocnicze/zabezpieczające:
        a. htmlspecialchars() – konwersja znaków specjalnych na encje HTML (ochrona przed XSS).
        b. trim() – usuwanie białych znaków z początku i końca ciągu.


## 5. _Integracja z bazą danych MySQL (mysqli) – Klucz do zadań INF.03

    I. Nawiązanie połączenia:
        a. $conn = mysqli_connect("localhost", "root", "", "nazwa_bazy");

        b. mysqli_connect_errno() / mysqli_connect_error() – weryfikacja poprawności połączenia.

    II. Ustawienie kodowania znaków:
        a. mysqli_set_charset($conn, "utf8"); – zapewnia poprawne wyświetlanie polskich znaków.

    III. Wykonanie zapytania SQL:

        a. $sql = "SELECT id, imie, nazwisko FROM uzytkownicy";
        b. $result = mysqli_query($conn, $sql);
            potem $row = mysqli_fetch_assoc['nazwa kolumny']

    IV. Przetwarzanie wyników (SELECT):

        a. mysqli_fetch_assoc($result) – pobiera kolejny wiersz jako tablicę asocjacyjną (np. $row['imie']).
        b. mysqli_fetch_row($result) – pobiera wiersz jako tablicę indeksowaną numerycznie ($row[0]).
        c. mysqli_num_rows($result) – zwraca liczbę pobranych wierszy.
        d. mysqli_affected_rows($conn) – zwraca liczbę zmienionych wierszy przy INSERT, UPDATE, DELETE.

    V. Zamknięcie połączenia:
        a. mysqli_close($conn);


## 6. _Zaawansowane mechanizmy (Sesje, Ciasteczka, Pliki)

    I. Sesje (mechanizm logowania/zapamiętywania stanu):
        a. session_start(); – musi znajdować się na samym początku pliku (przed jakimkolwiek kodem HTML nawet <!DOCTYPE html>).
        b. $_SESSION['user'] = "Jakub"; – zapisanie danych w sesji. 
            <?php
            session_start(); // Musi być na samej górze!

            // Załóżmy, że dane z formularza zgadzają się z bazą danych
            $wprowadzonyLogin = "Jakub"; 

            // Zapisujemy informację w sesji
            $_SESSION['user'] = $wprowadzonyLogin;

            // Przekierowujemy użytkownika na podstronę zabezpieczoną
            header("Location: panel.php");
            exit();
            ?>

            ("Location: panel.php"); :::
                <?php
                session_start(); // Wznowienie sesji

                // Sprawdzamy, czy zmienna 'user' jest ustawiona w sesji
                if (isset($_SESSION['user'])) {
                    // Jeśli tak, wyświetlamy spersonalizowaną treść
                    echo "Witaj w panelu administratora, " . $_SESSION['user'] . "!";
                    echo '<br><a href="wyloguj.php">Wyloguj się</a>';
                } else {
                    // Jeśli nie ma sesji, blokujemy dostęp
                    echo "Brak dostępu! Musisz się najpierw zalogować.";
                }
                ?>

        c. unset($_SESSION['user']); – usunięcie wybranej zmiennej sesyjnej.
            używamy gdy chcemy usunąć konkretną zmienną np. koszyk zakupowy
        d. session_destroy(); – np w przypadku wylogowania 

    II. Ciasteczka (Cookies):
        a. setcookie("nazwa", "wartość", time() + 3600); – ustawienie ciasteczka na 1 godzinę.
            <?php
            // UWAGA: setcookie() musi być przed jakimkolwiek HTML-em lub tekstem (echo)!
            setcookie("uzytkownik", "Jakub", time() + 3600);
            ?>

        b. $_COOKIE['nazwa'] – odczytanie wartości ciasteczka.
            <?php
            // session_start() tutaj nie jest potrzebne dla ciasteczek, ale zasada czystego kodu tak
            ?>
            <!DOCTYPE html>
            <html lang="pl">
            <head>
                <meta charset="UTF-8">
                <title>Odczyt ciasteczka</title>
            </head>
            <body>
                <h2>Odczytywanie ciasteczka:</h2>
                
                <?php
                if (isset($_COOKIE['uzytkownik'])) {
                    echo "Witaj, " . htmlspecialchars($_COOKIE['uzytkownik']) . "! Ciasteczko działa poprawnie.";
                } else {
                    echo "Brak ciasteczka. Najpierw odwiedź plik ustaw_ciastko.php!";
                }
                ?>
            </body>
            </html>

    III. Przesyłanie plików z formularza:
        a. <form ......................... enctype="multipart/form-data"> – wymagany atrybut w HTML.
        b. $_FILES['plik']['name'], $_FILES['plik']['tmp_name'], $_FILES['plik']['size'] – parametry przesłanego pliku.
            * $_FILES['nazwa']['name']     -> oryginalna nazwa pliku
            * $_FILES['nazwa']['tmp_name'] -> ścieżka tymczasowa na serwerze
            * $_FILES['nazwa']['size']     -> rozmiar w bajtach
            * $_FILES['nazwa']['type']     -> typ pliku (MIME)
            * $_FILES['nazwa']['error']    -> kod błędu (0 = brak błędów)

        c. move_uploaded_file($tmp, $docelowa_sciezka) – przeniesienie pliku z folderu tymczasowego na serwer.
                if (isset($_FILES['plik'])) {
                $tmp = $_FILES['plik']['tmp_name'];
                $nazwaPliku = $_FILES['plik']['name'];
                
                // Określamy ścieżkę, gdzie plik ma trafić na stałe
                $docelowaSciezka = "upload/" . $nazwaPliku;
                
                // Przenosimy plik z folderu tymczasowego
                if (move_uploaded_file($tmp, $docelowaSciezka)) {
                    echo "Sukces! Plik został zapisany na serwerze.";
                } else {
                    echo "Błąd podczas przenoszenia pliku!";
                }
            }

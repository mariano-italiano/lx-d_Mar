# Kroki uruchamiania kontenera

1. Pobranie obrazu z rejestru, pod warunkiem że nie został już wcześniej pobrany.
2. Utworzenie kontenera.
3. Załadowanie systemu plików i utworzenie warstwy do odczytu i zapisu (r/w).
4. Zainicjalizowanie sieci (mostka sieciowego/bridge'a)
5. Konfiguracja sieci (przypisanie adresu IP).
6. Uruchomienie kontenera = zadania.
7. Przechwytywanie wyjścia - `docker logs`.

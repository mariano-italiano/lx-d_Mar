## Dockerfile Best Practices

- używaj tylko oficialnych obrazów jeśli możliwe + hardening
- Alpine nie zawsze jest najlepszym wyborem - chociaż Alpine jest lekki, istnieją pewne znane problemy z wydajnością niektórych technologii oraz luki bezpieczeństwa (https://pythonspeed.com/articles/alpine-docker-python/)
- ogranicz ilość warstw obrazu - każda instrukcja `RUN` w pliku Docker spowoduje utworzenie dodatkowej warstwy w ostatecznym obrazie, najlepszą praktyką jest ograniczenie liczby warstw, aby zachować lekkość obrazu
- uruchamianie jako użytkownik inny niż root - uruchamianie kontenerów jako użytkownik niebędący rootem znacznie zmniejsza ryzyko eskalacji uprawnień kontener -> host
- nie używaj taga `latest` - użyj konkretnej wersji obrazu, używając `major.minor`, a nie `major.minor.patch`, aby zawsze mieć pewność, że najnowsze aktualizacje zabezpieczeń są zawarte w nowo tworzonych obrazach
- zawsze łącz `apt-get update` z `apt-get install` w pojedynczej instrukcji `RUN` - użycie samego `apt-get update` w `RUN` powoduje problemy z buforowaniem i kolejne instrukcje `apt-get install` kończą się niepowodzeniem. Jest to związane z mechanizmem buforowania używanym przez Dockera. Podczas budowania obrazu, Docker widzi początkowe i zmodyfikowane instrukcje jako identyczne i ponownie wykorzystuje pamięć podręczną z poprzednich kroków. W rezultacie aktualizacja `apt-get` nie jest wykonywana, ponieważ kompilacja używa wersji buforowanej. Ponieważ aktualizacja apt-get nie jest uruchamiana, kompilacja może potencjalnie uzyskać nieaktualną wersję pakietów.
- używanie statycznych identyfikatorów UID i GID (dyskusyjne)

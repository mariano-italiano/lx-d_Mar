FROM ubuntu:20.04

# Utwórz usera app oraz grupe app
RUN groupadd -g 2500 appgroup && useradd -u 2500 -m -g appgroup appuser

# Uruchomienie kontenera jako 'appuser'
USER appuser

# Ustawienie workdir'a
WORKDIR /home/appuser

# Uruchom komende 'tail -f /dev/null' przy starcie kontenera
ENTRYPOINT ["tail"]
CMD ["-f", "/dev/null"] 


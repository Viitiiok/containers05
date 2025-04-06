# containers05

## Scopul lucrării
Interacțiunea între mai multe containere Docker, între un container Nginx și un container PHP.

## Sarcina
Sarcina principală a fost crearea unei aplicații PHP bazate pe două containere: Nginx și PHP, care să comunice între ele într-o rețea internă Docker.

## Descrierea efectuării lucrării
Pregătirea inițială
1. Am instalat Docker pe calculatorul personal
2. Am recapitulat cunoștințele din lucrarea de laborator №3
3. Am creat un director pentru proiect și am inițializat un repo

## Configurarea proiectului
Am creat structura de directoare
Am configurat fișierul .gitignore pentru a exclude conținutul directorului mounts/site/
Am creat configurația Nginx în nginx/default.conf care:
Ascultă pe portul 80
Servește fișiere din /var/www/html
Procesează cererile PHP prin trimiterea lor către containerul PHP

## Pornirea și testarea
Am creat rețeaua Docker internal:

bash
Copy
docker network create internal
Am lansat containerul PHP (backend):

Am lansat containerul Nginx (frontend):

## Concluzii
Prin această lucrare am învățat cum să configurăm și să gestionăm interacțiunea între containere Docker. Am stabilit o comunicare eficientă între un server web Nginx și un procesor PHP.

## Răspunsuri la întrebări
1. În ce mod în acest exemplu containerele pot interacționa unul cu celălalt?
Containerele interacționează prin rețeaua Docker internal. Nginx trimite cererile PHP către containerul PHP folosind numele serviciului în configurația fastcgi_pass.

2. Cum văd containerele unul pe celălalt în cadrul rețelei internal?
În cadrul rețelei internal, containerele se pot rezolva reciproc prin nume. Astfel, containerul Nginx poate accesa containerul PHP folosind numele backend.

3. De ce a fost necesar să se suprascrie configurarea nginx?
Configurația implicită a Nginx nu știe să gestioneze cererile PHP sau unde să trimită aceste cereri. A fost necesar să configurăm:

+++
date = '2026-11-04T12:29:40Z'
draft = false
title = 'Einführung'
+++


# Einführung

Ein wenig Theorie zum Anfang. 

## Was sind (Docker-) Container?

Container sind eine Leichtgewichtige virtualisierungs Technik. Docker war die erste große Container Engine, welche Container angeboten hat. Der Name Docker wird bei Containern häufig als synonym genutzt, ähnlich wie Tempo für Taschentücher. Mitlerweile gibt es viele Container Engines, vor allem bei Kubernetes wird gar nicht mehr auf die Dockerengine gesetzt.

In diesem Kurs werden wir [Podman](https://podman.io) von RedHat verwenden. Fast alles was mit Docker geht, geht auch mit Podman und RedHat ist so freundlich es kostenlos rauszugeben. Docker Desktop für Windows und Mac ist im Unternehmenskontext heufig nicht kostenlos.  

Ein Container Image ist einfach gesprochen, ein Linux Dateisystemimage. Dies kann zum Beispiel ein Abbild von einem RedHat Linux sein, dann würde man von einem Base Image sprechen. Auf diesem Image bauen viele andere Images auf, so würde eine Python Anwendung wahrscheinlich ein Image nutzen, auf dem Python schon installiert ist.

Dieses wird mit Hilfe von change root (chroot) zu einer isolierten Laufzeitumgebung für Prozesse. Wenn du damit nichts anfagen Kannst ist das Okay, wichtig ist, dass der Prozess auf dem Hostsystem ausgeführt wird und nicht in einer neuen Virtuellen Maschine. 

### [Lab 1]: Starten eines Container Imagages 

Wir gehen davon aus, dass Podman bereits installiert ist, wenn nicht bitte unter [Podman.io](https://podman.io) nachsauen wie es auf euerem System funktioniert. Sollte Docker bereits installiert sein, könnte ihr auch in dem Befehl podman durch docker ersetzen.  

Für ein einfaches Hello World, muss folgender Befehl im terminal ausgeführt werden:
``` bash
podman run quay.io/podman/hello
```

{{% details summary="Output" %}}

``` bash
Trying to pull quay.io/podman/hello:latest...
Getting image source signatures
Copying blob sha256:1ff9adeff4443b503b304e7aa4c37bb90762947125f4a522b370162a7492ff47
Copying config sha256:83fc7ce1224f5ed3885f6aaec0bb001c0bbb2a308e3250d7408804a720c72a32
Writing manifest to image destination
!... Hello Podman World ...!

         .--"--.
       / -     - \
      / (O)   (O) \
   ~~~| -=(,Y,)=- |
    .---. /`  \   |~~
 ~/  o  o \~~~~.----. ~~
  | =(X)= |~  / (O (O) \
   ~~~~~~~  ~| =(Y_)=-  |
  ~~~~    ~~~|   U      |~~
```

{{% /details %}}

Was ist Passiert? Podman hat das Image *hello:latest* des Accounts *podman* von der Container Regestry *quay.io* gedownloaded und gestartet. Die STDOUT (Standard out ausgabe des Programmes wird ausgegeben).
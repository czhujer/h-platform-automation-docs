# C&C server
- command and control server

Nejaka mensi service (s HTTP API), ktera bude oddelena od zbytku a odlazena.

Neco ala https://falconframework.org/ pro python, ci https://mojolicious.org/ pro perl.
v PHP cekam staci pouzivat zaklad symfony a nejake moduly okolo ci slim framework.
Sluzba zrejme bude zit na HQ-server(u), jelikoz musi byt dostupna z Inetu po IP (resp HTTP/S).

Jednak bude tato sluzba zpracovavat webhook od calculoid pluginu (ktery bude na webu).
Po parsingu informaci (produkt_id, zakaznik,..) pak zavola jenkins server.
Jenkins ma API, nebo primo URL na dany job (s tokenem, kde pak neni treba jenkins user).
Posleze se provedou dalsi akce (poslani mailu, zapis info od CRM systemu).

V dalsi fazi (v2 arch) bude nahrazovat funkci jenkins serveru a volat dalsi casti systemu.
Dalsimi castmi systemu je mysleno proxmox provisining server, terraform apod.
Tj. bude pridano Rest API (pripadne i gRPC).

Mozna v ramci zpetne kompatibity bude volat jenkins server (v1 arch).

V navrhu je treba pocitat s podporou prometheus sdk a opentracing (jaeger).

V dalsich fazich je pocitano v frontendem (React, Vue.js).

# Labb – Git, Virtuell Labbmiljö & Nätverk

## 1. Introduktion

Jag genomför denna labb för att träna på Git, virtuella
maskiner, nätverkskonfiguration och kommandoradsarbete.

###

Niklas Åberg - 2026-09-30 - ICSX26

## 2. Labbmiljö & Nätverk

Jag använder VirtualBox som hypervisor.

### Linux-VM

Operativsystem: Ubuntu Server  
IP-adress: 192.168.1.50  
Subnetmask: 255.255.255.0

### Windows-VM

Operativsystem: Windows 11  
IP-adress: 192.168.1.51  
Subnetmask: 255.255.255.0


### VMs

Jag använder tidigare installeringar av Ubuntu och Win11 som installerats under tidigare tillfälle.


### VM Internt Nätverk

Jag har nu skapat ett internt nätverk för båda mina VMs som heter 'LabNetwork' och skall nu konfigurera deras IP-addresser

### Windows Internt Nätverk

Jag har nu konfigurerat min Windows 11 VM för att ha korrekt IP för uppgiften.

### Ubuntu Konfig

Jag har nu konfigurerat korrekt IP i ubuntu, jag skall nu starta ping tester mellan VMsen.

### Pingtester

Jag utförde pingtester mellan Win11 och Ubuntu VM och fick problem med windows brandväggen men efter jag skapade en exception för detta så fungerar allt fint.

## Linux / Bash

Jag skapade en mapp och submapp som heter Systementor och konsultdata, i denna mapp skapade jag anteckningar.txt

### Skapar grupp 'Konsulter'

Jag har skapat en grupp som heter Konsulter med hjälp av sudo groupadd konsulter och sedan dubbelkollat så att den finns med getent group konsulter.

### Behörigheter

Jag ger behörigheter och ändrar gruppägare för gruppen med sudo chown och sudo chmod och dubbelkollade sedan detta med ls -la /var/systementor/konsultdata.

## Windows - Powershell

### Skapa Mapp 

Jag använder mig av New-Item för att skapa en mapp i C:\ som heter Systementor och en submapp som heter Konsultdata

### ACL Lista

Jag använder mig av get-acl för att få information om Path, Owner och Access.

### Verifiering

Jag har verifierat nätverksanslutningen mellan Linux VM och Win11 VMen.

## AI-logg och Utvärdering:

Jag ställde frågan: Kan du förklara funktionen ipconfig och hur det hjälper mig vid nätverksproblem?
Och fick tillbaka följande svar från ChatGPT som jag valde att fråga:

### AI SVAR

Absolut. ipconfig är ett Windows-kommando som visar och hjälper dig hantera datorns nätverkskonfiguration. Det är särskilt användbart när internet eller det lokala nätverket inte fungerar som det ska.
Grundläggande användning

Öppna Kommandotolken (cmd) och skriv:

ipconfig

Du får bland annat se:

    IPv4-adress – datorns adress på nätverket, exempelvis 192.168.1.25.

    Nätmask (Subnet Mask) – anger vilket nätverk datorn tillhör.

    Default Gateway – vanligtvis routerns IP-adress. Datorn använder den för trafik utanför det lokala nätverket.

    IPv6-adress – motsvarande adressformat för IPv6.

Några särskilt användbara kommandon

Se all nätverksinformation:

ipconfig /all

Det ger bland annat DNS-servrar, DHCP-information och MAC-adress.

Förnya IP-adressen:

ipconfig /release
ipconfig /renew

Det kan hjälpa om datorn har fått en felaktig eller oanvändbar IP-adress från routerns DHCP-server.

Rensa DNS-cachen:

ipconfig /flushdns

Det kan vara användbart om datorn hittar vissa webbplatser felaktigt eller inte kan översätta ett domännamn till rätt IP-adress.
Exempel på felsökning

Om du inte kommer ut på internet kan du börja med:

ipconfig

Om du exempelvis ser en adress som börjar med 169.254... kan det tyda på att datorn inte lyckats få en IP-adress från DHCP-servern/routern.

Sedan kan du testa routern:

ping 192.168.1.1

(Byt ut adressen mot den som står som Default Gateway hos dig.)

    Fungerar ping → datorn kan nå routern.

    Fungerar den inte → problemet kan ligga mellan datorn och det lokala nätverket.

    Fungerar routern men internet inte gör det → problemet kan ligga längre ut, exempelvis DNS eller internetanslutningen.

Kort sagt: ipconfig hjälper dig att ta reda på vilken nätverksadress datorn har, vilken router den använder och hur nätverkskonfigurationen ser ut. Det gör det mycket lättare att avgöra var ett nätverksproblem uppstår.

### Tankar om AI svar

Jag tycker att information som ChatGPT gav mig i denna fråga var konsis och stämde överens bra med sanningen, den hallicunerade ingenting, den var lite väl kort i vad skillnaden är mellan ipv4 och ipv6 är för något och det hade ju varit extra bra men ingenting jag bad den om.
Den förklarar inte heller speciellt utförligt hur de kommandona fungerar utan bara vad de gör vilket kan skapa problem om personen som frågar kanske inte vet exakt vad som händer ifall man använder de på fel sätt.
Jag valde att fråga ChatGPT något som jag personligen hade koll på hur det funkar så att jag själv kunde verifiera att informationen stämmer.
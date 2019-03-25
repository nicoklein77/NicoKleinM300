*
# Dokumentation LB2
*M300 von Nico Klein*
*
## Inhaltsverzeichnis
  - [Inhaltsverzeichnis](#inhaltsverzeichnis)
  - [Persönlicher Wissensstand](#pers%C3%B6nlicher-wissensstand)
  - [Umgebung](#umgebung)
  - [Vorgefertigte VM mit Vagrant aufsetzen](#vorgefertigte-vm-mit-vagrant-aufsetzen)
  - [Vagrant Ubuntu VM mit Firewall und Webserver](#vagrant-ubuntu-vm-mit-firewall-und-webserver)
  - [Wissenswachstum](#wissenswachstum)
  - [Reflexion](#reflexion)
  - [Quellen](#quellen)
  

*
## Persönlicher Wissensstand
*Virtualisierung*  
Bis jetzt bloss mit VMWare gearbeitet. In vielen ÜKs habe ich diverse virtuelle Maschinen aufgesetzt, konfiguriert und verwendet. Im privaten Bereich wenig Virtualisierung genutzt. 
Fazit: Bis jetzt gute Kenntnisse gesammelt 
*Vagrant*  
Vagrant habe ich im jetzigen Modul kennengelernt.  
Fazit: Alles neu für mich.  
*Git*  
Github Habe ich bereits im Geschäft verwendet und kenne die funktionen.  
Fazit: Bereits Kenntnisse mit Pushen und Clonen eines Repos.  
*Linux*  
Bisher in der TBZ verschiedene Maschinen aufgesetzt, wie auch im Geschäft bereits einige Mashcinen verwendet.  
Fazit: Nicht neu, aber auch nicht die grössten Kenntnisse.  
*Systemsicherheit*  
Ich hatte bereits ein üK welcher sich explizit mit dem beschäftigte. Des Weiteren bin ich im Geschäft damit beschäftig unser System auf sicherheitslücken zu prüfen, weshal ich in diesem Thema bereits gute Kenntnisse habe.  
Fazit: Gute Kenntnisse.  
*Markdown*  
Markdown habe ich in diesem Modul kennengelernt, vorher noch nicht gekannt.  
Fazit: Sehr neu für mich.  

*
## K1: Umgebung auf eigenem Notebook eingerichtet und funktionsfähig   

*Git*  
Nach Anleitung des M300-Repositories gemacht:  
Github  
  1. Auf www.github.com Benutzerkonto erstellt
  2. Bestätigungsemail bestätigt und Anmeldung getestet.  

Repository erstellen  
  1. "New Repository" ausgewählt
  2. Name vergeben: M300-Repo
  3. Public gemacht
  4. "Initialize this repository with a README" ausgewählt
  5. "Create a repository" wählen um Erstellung fertig zu stellen.  
  
Git Hub  
  1. Git 2.20.1 installiert (Mit Admin-Rechten)
  2. Standardinstallation
  3. Geöffnet und konfiguriert:  
    >$ git config --global user.name "<nicoklein77>"  
    >$ git config --global user.email "<snackbar.spastim@hotmail.com>"  

SSH-Key  
  1. Im Git Bash Termin:
    >ssh-keygen -t rsa -b 4096 -C "snackbar.spastim@hotmail.com"  
    >Enter a file in which to save the key (~/.ssh/id_rsa):  
    (Einfach Enter drücken)  
    >Enter passphrase (empty for no passphrase):  
    (Kennwort definieren)  
    >Enter same passphrase again:  
    (Kennwort erneut eingeben)  
   2. %HOME%/.ssh/id_rsa.pub mit Notepad öffnen und Schlüssel kopieren  
   3. Github Website öffnen und dort unter Settings/SSH den Schlüssel angebennd GPG keys angeben  
   
Repository klonen  
Modulrepository:  
    > git clone https://github.com/mc-b/M300.git  
    > cd M300  
    > git pull  
    > git status  
    
Mein Repository:  
    >git clone https://github.com/nicoklein77/NicoKleinM300
    > git pull --> Um zu aktualisieren  
    > git status --> Um  Status der lokalen Kopie anzuzeigen  

*VirtualBox*  
Mit Hilfe von VirtualBox können Virtuelle Maschinen erstellt und verwaltet werden.  
VirtualBox ist eine Opensource-Virtualisierungssoftware.  
Da in diesem Modul keine speziellen Einstellungen notwendig sind, kann bei der Installation einfach die Standardinstallation verwendet werden.  

*Vagrant*  
Mit Hilfe von Vagrant kann man in VirtualBox automatisiert VMs und Services installieren lassen.  
Genau wie bei Virtualbox kann hier die Standart-Installtion verwendet werden.  

Wichtige Befehle  

Vagrantfile erstellen und Umgebung initialisieren  
> vagrant init  

Konfigurierung und Erstellung einer VM mit Vagrantfile  
> vagrant up  

Verbindung via SSH herstellen  
> vagrant ssh

Status der VM anzeigen  
> vagrant status

VM pausieren/stoppen  
> vagrant halt

VM zerstören  
> vagrant destroy

*VisualStudio Code*  
VisualStudio Code ist ein Texteditor von Microsoft.  
Mit VisualStudio kann man ein Repository direkt öffnen und wenn man fertig ist kann man es auch gleich wieder pushen (dafür werden aber Extensions benötigt).  
Bei der Installation von VisualStudio mussten wir für dieses Modul keine speziellen Angaben berücksichtigen; also Standardinstallation.  
*Benötigte Extensions:*  
  - Markdown All in One  
  - Vagrant Extension  
  - vscode-pdf Extension  
  
Diese Extensions werden dazu benötigt damit diese Dokumentation und das Vagrant-file einfacher bearbeitet werden können.  
Diese Extensions werden wie folgt installiert:  
  1. VisualStudio Code öffnen  
  2. ExtensionMenu öffnen (Abkürzung: Ctrl+Shift+X)  
  3. Gewünschte Extension suchen und installieren  

##  Vorgefertigte VM mit Vagrant aufsetzen

Aus dem M300 Repository, setzte ich automatisiert eine Ubuntu VM mit Apache2 auf.
Dazu musste ich nur in das Verzeichnis /M300/vagrant/web wechseln und "vagrant up" ausführen. 
Die VM wird daraufhin installiert und in Virtualbox angezeigt. 

## Vagrant Ubuntu VM mit Firewall und Webserver

*Konfiguration*  

Um die Firewall und den Webserver zu installieren und konfigurieren habe ich das Vagrant File folgendermassen angepasst.  
Es wird ubuntu xenial64 als Basis verwendet.
  >Vagrant.configure("2") do |config|  
  >config.vm.box = "ubuntu/xenial64"

Es wird ein privates Netzerk erstellt. (Host Only) Als Ip habe ich ein eine einfache Klasse C Ipv4-Adresse verwendet: 10.10.0.20 /24.  
Für mich definierte IP wird konfiguriert.  
  >config.vm.network "private_network", ip: "10.10.0.20"

Da dies der Ordner ist in dem der Webserver das html Dokument bezieht, kann ich im vornherein ein index file in den Ordner einfügen, welches vom Webserver verwendet werden wird.
  >config.vm.synced_folder ".", "/var/www/html"

Virtualbox wird als VMprovider genutzt
  >config.vm.provider "virtualbox" do |vb|

Es werden 4 GB Ram zur Verfügung gestellt-  
  >vb.memory = "2048"  
  >end  

Diese ganzen Einstellungen wurden im Vagrantfile eingefügt damit beim ausführen alle Einstellungen übernomen werden

Installieren von Apache2 und ufw. ufw erlaubt Ports von ssh und http und IPs vom 24-Netz 10.10.0.0
 >  config.vm.provision "shell", inline: in der SHELL ausführen  
 >  apt-get update  
 > apt-get install -y apache2  
 >apt-get update  
 >apt-get install -y ufw  
 >ufw allow ssh  
 >ufw allow http  
 >ufw allow from 10.71.13.0/24  

Da ein Neustart unerwünscht ist, wird die Firewall manuell eingeschaltet. yes Y | führt dazu, dass die Abrage beim enablen mit Y beantwrtet wird.
  >   yes Y | ufw enable  
  > SHELL  
  >end  

*Sicherheit* 
Der Zugriff über SSH ist standardmässig möglich.
Beim automatisierten Aufsetzen, wird ein neuer SSH-Key generiert.  
Die Firewall ist erlaubt den Zugriff über SSH und HTTP. Zusätzlich habe ich festegelegt, dass nur IPs aus dem Subnetz 10.10.0.0 zugreifen dürfen.

*Starten* 
Die VM kann mit vagrant up gestartet werden, wenn man die Konsole im Ordner mit dem Vagrantfile ausführt.  
Danach wird durch vagrant ssh eine Verbindung hergestellt.

*Aufsetzen*
Im Ordner Vagrant folgenden Befehl ausführen und die VM wird verbunden.
>vagrant up  

## Wissenswachstum

*Virtualisierung*  
Da wir in diesem Modul mit Virtualbox geabrietet haben und ich dies bisher noch nicht verwendet habe, kenne ich diese Software nun um einiges besser. 
Fazit: Mehr Kenntnisse über VirtualBox gesammelt  
*Vagrant*  
Habe ich bis jetut nicht gekannt, ich weiss nun wie ich automatisiert VMs erstellen, bearbeiten und wieder löschen kann.  
Fazit: Viele neue Befehle und funktionen dieser Sofware kennengelernt.  
*Git*  
Github Habe ich, wie bereits erwähnt im Geschäft verwendet.  
Fazit: Keine weitere Kenntnisse gesammelt.  
*Linux*  
Ich kenne nun einen Webserver, eine Firewall und einen einfachen Host welcher auf Linux bassiert.  
Fazit: Habe bereits solche Maschinen aufgesetzt, jedoch nicht automatisiert.  
*Systemsicherheit*  
Durch dieses Modul habe ich einige wichtige, neue Aspekte in der Systemsicherheit kennengelernt.    
Fazit: Viele neue Erfahrungen gesammelt und weiss nun auf was man einen Wert legen sollte.  
*Markdown*  
Ich weiss nun wie ich ein Markdown-File erstellen und Codieren muss, damit es im Browser übersichtlich angezeigt wird.  
Fazit: gelernt wie ich mit einem Markdown-File eine Dokumentationen gestallten kann.

## Reflexion

Am Anfang des Moduls startete es gut, da ich das Pushen und Klonen des Repos bereits kannte und die funktionen welche es beinhaltete konnte ich schnell starten und mit der erstellung der VMs über Vagrant beginnen und mich damit auseinanderer setzen.
Das Dokumentieren mit Markdown kannte ich bisher noch nicht, dies beanspruchte eine gewisse Zeit bis ich die Syntax verstanden habe. 
Gegen Ende des Modul verlor ich mein Gerät auf welchem ich meine VMs samt konfiguration hatte, mein Vagrant file, meine Markdown Dokumentation und den Login für GitHub. Dies musste ich innerhalb von kürzerer Zeit nacharbeiten, ich erstellte nochmals einen Login auf Github, einen Teil der Markdown Doku hatte ich noch was mir sehr geholfen hat. Ich erstellte mit Vagrant nochmals einen Teil der VMs und dokumentierte dies so gut wie möglich.
Fürs nächste mal speichere ich gleich von beginn ab alle meine Daten im Web und nicht nur lokal auf einem Gerät, da genau dies passieren kann.


## Quellen

* <https://github.com/mc-b/M300>  
* <https://bscw.tbz.ch/bscw/bscw.cgi/20886245>
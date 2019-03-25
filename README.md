*
# Dokumentation LB2
*M300 von Nico Klein*
*
## Inhaltsverzeichnis
- [Dokumentation LB2](#dokumentation-lb2)
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
    >$ git config --global user.email "<>"  

SSH-Key  
  1. Im Git Bash Termin:
    >ssh-keygen -t rsa -b 4096 -C ""  
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
    >git clone  
    > git pull --> Um zu aktualisieren  
    > git status --> Um  Status der lokalen Kopie anzuzeigen  

*VirtualBox*  
Mit Hilfe von VirtualBox können Virtuelle Maschinen erstellt und verwaltet werden.  
VirtualBox ist eine Opensource-Virtualisierungssoftware.  
Da in diesem Modul keine speziellen Einstellungen notwendig sind, kann bei der Installation einfach die Standardinstallation verwendet werden.  

*Vagrant*  
Mit Hilfe von Vagrant kann man in VirtualBox automatisiert VMs und Services installieren lassen.  
Wie mit VirtualBox werden hier keine speziellen Einstellungen bei der Installation gebraucht, deshalb kann man die Standardinstallation verwenden.  

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


*
## Wissenswachstum
asdasd

*Git*
Ich habe gelernt was, Git, Repositories und Markdown sind. Wie man Repositories bearbeitet, klont und auch lokal absichert, und auch die Sprache Markdown und wie sie funktioniert.  
Fazit: Ich kannte Git und Repositories vorher garnicht und kenne mich jetzt ziemlich gut aus. Desweiteren habe ich eine neue Sprache kennengelernt.
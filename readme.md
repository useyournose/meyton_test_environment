Wer eine Scheibenanlage der Firma Meyton hat, bekommt auch Zugriff auf eine Umgebung zum testen.
Diese besteht aus
- Workstation (zentraler Server)
- Control PC (Scheibenanzeige)
- Gateway (simuliert bis zu 10 Meßrahmen).

Die gesamte Infrastruktur arbeitet mit fixen IP Zordnungn.

Mein gewähltes Setup habe ich in VirtualBox auf Windows installiert.

Ein zweites Gateway ist schnell aufgesetzt, doch im Gegensatz zu den ControlPCs verfügt dieses nicht über eine Grafische Bedienoberfläche.
So muß man die Einstellungen über die Kommandozeile anpassen

1. Gateway klonen, den Klon starten
2. per ssh auf das Gateway zugreifen.
3. die zu ändernden Dateien liegen im mountpoint /flash. Dieser muß zuerst als Read/write mountpoint eingebunden werden
- mount -o remount,rw /flash
4. nun die gewünschte IP Adresse in die Datei /flash/syslinux.cfg eintragen, diese dazu mit einem Editor öffnen
- vi /flash/syslinux.cfg
- nach der bearbeitung, speichern nicht vergessen.
5. die Zuweisungen der seriellen Schnittstelle findet über die routes Datei statt. Diese einfach in einem Editor öffnen, und jeweils das letzte Oktet der Meßrahmen eintragen.
- vi /flash/meyton/routes
- nach der bearbeitung, speichern nicht vergessen.
6. mit dem Befehl Reboot, den Rechner neu starten. - Die ssh Verbindung wird automatisch geschlossen.

Nun die gewünschte Menge an Control PC klonen, starten und entsprechend der Wünsche mit IP's und rangeID ausstatten.

Done.

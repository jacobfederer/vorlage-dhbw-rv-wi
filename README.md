# Vorlage für Wissenschaftliche Arbeiten der DHBW Ravensburg / Wirtschaftsinformatik
Diese LaTeX Vorlage dient als Grundlage für wissenschaftliche Arbeiten an der DHBW Ravensburg in der Fakultät für Wirtschaft im Studiengang Wirtschaftsinformatik.

Die Vorlage orientiert sich an den Gestaltungsrichtlinien der DHBW RV.

### Enthaltene Titelblätter:                                                
 - Seminararbeit    
 - Projektarbeit
 - Bachelorarbeit
 - Projektdokumentation

## Benutzung
Um die Vorlage zu benutzen, kannst du sie einfach hier Downloaden.
Das .zip entpacken und den Inhalt in dein gewünschtes Arbeitsverzeichnis kopieren. (siehe: [Versionierung und Backup](## Versionierung und Backup))

## Installation MacOS
TBD
short:
- download and install [MacTex](https://tug.org/mactex/)
- download and install [TechnStudio](http://www.texstudio.org/)
- be happy
## Installation Linux
TBD
short:
- download and install [TexLive](https://www.tug.org/texlive/)
- download and install [TexStudio](http://www.texstudio.org/)
- be happy

### Debian Based (bspw. Ubuntu):
```
sudo apt-get install texlive-full
```

## Installation Windows
TBD (wer benutzt schon freiwillig windows)
- download and install [MikTex](http://miktex.org/)
- download and install [TexStudio](http://www.texstudio.org/)
- switch to Linux or MacOs
- think about how much the last step impacted your live in terms of happiness!

## Konfiguration TexStudio
Konfiguration für TeXstudio: <br>
Unter: Preferences/erzeugen/Benutzerbefehle:
einen neuen Befehl mit folgendem Inhalt anlegen:
```bash
txs:///bibtex | txs:///makeindex "%.idx" -t "%.ilg" -o "%.ind" | txs:///makeindex -g -s "styles/stichwortverzeichnis.ist" % | txs:///makeindex "%.nlo" -s nomencl.ist -o "%.nls" | txs:///makeindex  -s "%.ist" -t "%.glg" -o "%.gls" "%.glo"
```
Anschließend mit Tools/benutzer/key kompilieren.									  

## Allgemeine Informationen zum Gebrauch
Keine Änderungen an den Dateien im Verzeichnis ```./pages/``` vornehmen. Für die Arbeit beziehen sich alle Änderungen auf diese Datei und die Dateien im Verzeichnis ```./chapter/```.

### Verzeichnisstruktur
Die Verzeichnisstruktur sieht folgendermaßen aus:
```
.
├── LICENSE.txt                 # Die Lizenz dieser Vorlage
├── README.md                   # Die Datei die du gerade liest
├── chapter                     # Dein Arbeitsverzeichnis
│   ├── 10_einleitung.tex       # Beispiel Datei mit beispielen
│   ├── 20_kapitel.tex          # Beispiel Kapitel
│   ├── 30_anhang.tex           # Die Datei in der dein Anhang definiert ist
│   ├── 30_artefact.pdf         # Eine PDF für den Anhang
│   ├── 80_fazit.tex            # Beispiel Fazit
│   └── glossary_collection.tex # Datei in der du dein Glossar definierts
├── images
│   └── jubilaeum.jpg           # Beispiel Bild
├── literatur
│   └── literatur.bib           # Deine Literatursammlung
├── pages                       # Vorlagen Verzeichnis! Nichts Ändern!
│   ├── 10_titel_bachelor.tex
│   ├── 10_titel_projekt.tex
│   ├── 10_titel_projekt_doku.tex
│   ├── 10_titel_seminar.tex
│   ├── 11_sperrvermerk.tex
│   ├── 12_inhaltsverzeichnis.tex
│   ├── 13_abkuerzungsverzeichnis.tex
│   ├── 14_glossar.tex
│   ├── 15_abbildungsverzeichnis.tex
│   ├── 16_tabellenverzeichnis.tex
│   ├── 17_listingsverzeichnis.tex
│   ├── 18_literaturverzeichnis.tex
│   ├── 19_index.tex
│   └── 20_erklaerung.tex
├── styles                     # Besondere Styles für die Vorlage
│   └── stichwortverzeichnis.ist
├── vorlage.pdf                # Output Datei (heißt wie hauptdatei)
└── vorlage.tex                # Hauptdatei <- Öffnen zum bearbeiten
```
### Initiale Konfiguration
In der Datei: ```vorlage.tex``` muss folgender bereich mit deinen persönlichen angaben ausgefüllt werden:
```TeX
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%% Konfiguration %%

\def\myType{1}
%% 0=Seminararbeit   %%
%% 1=Projektarbeit   %%
%% 2=Bachelorarbeit  %%
%% 3=Projektdokumentation %%

\def\myTopic{Titel}
\def\mySubTopic{Untertitel}
\def\myAutor{Vorname Nachname}
\def\myProf{Betruer Name}
\def\myEndDate{Abgabe Datum}

%% Bachelorarbeit und Projektarbeit %%
\def\myCompany{Unternehmensname}
\def\myCompanyAddressStreet{Unternehmen Anschrift}
\def\myCompanyAddressCity{Stadt des Unternehmenssitzes}

%% Seminararbeit %%
\def\myVorlesung{Vorlesungstitel}

%% Projektarbeit %%
\def\myProjNumber{2}         % [1|2]
\def\myPraxPhase{2}          % [1|2|3]
```
#### Die Befehle im Einzelenen
```
\def\myType{1}
```
Gibt an welche art von Projekt geschrieben wird. Dadurch wird das entsprechende Titelblatt mit den nachfolgenden Informationen befüllt.
folgende werte können verwendet werden:
- {0} [Seminararbeit](##### Seminararbeit)
- {1} [Projektarbeit](##### Projektarbeit)
- {2} [Bachelorarbeit](##### Bachelorarbeit)
- {3} [Projektdokumentation](##### Projektdokumentation)

##### Allgemeine Informationen

| Befehl                          | variable              | Erläuterung                                           |
| ------------------------------- |:---------------------:| ----------------------------------------------------- |
| `\def\myType{1}`                | **_1_**               | Art der Arbeit                                        |
| `\def\myTopic{Titel}`           | **_Titel_**           | Der Titel der Arbeit                                  |
| `\def\mySubTopic{Untertitel}`   | **_Untertitel_**      | Der Unteritel der Arbeit (falls vorhanden)            |
| `\def\myAutor{Vorname Nachname}`| **_Vorname Nachname_**| Vorname und Nachname des Autors                       |
| `\def\myProf{Betruer Name}`     | **_Betreuer Name_**   | Titel Vorname und Nachname des Betreuenden Lehrkörpers|
| `\def\myEndDate{Abgabe Datum}`  | **_Abgabe Datum_**    | Abgabedatum der Arbeit                                |

##### Seminararbeit
Spezielle befehle für eine Seminararbeit:

| Befehl                              | variable              | Erläuterung                                           |
| ----------------------------------- |:---------------------:| ----------------------------------------------------- |
| `\def\myType{0}`                    | **_0_**               | Option **0** ist Seminararbeit                        |
| `\def\myVorlesung{Vorlesungstitel}` | **_Vorlesungstitel_** | Titel der Vorlesung                                   |

##### Projektarbeit

| Befehl                              | variable              | Erläuterung                                           |
| ----------------------------------- |:---------------------:| ----------------------------------------------------- |
| `\def\myType{1}`                    | **_1_**               | Option **1** ist Projektarbeit                        |
| `\def\myCompany{Unternehmensname}` | **_Unternehmensname_** | Name des betreuenden Unternehmens                                  |
| `\def\myCompanyAddressStreet{Unternehmen Anschrift}` | **_Unternehmen Anschrift_** | Straße Hausnummer Unternehmenssitzes                                 |
| `\def\myCompanyAddressCity{Stadt des Unternehmenssitzes}` | **_Stadt des Unternehmenssitzes_** | PLZ Stadt Unternehmenssitzes                                   |

##### Bachelorarbeit

| Befehl                              | variable              | Erläuterung                                           |
| ----------------------------------- |:---------------------:| ----------------------------------------------------- |
| `\def\myType{2}`                    | **_2_**               | Option **2** ist Bachelorarbeit                        |
| `\def\myCompany{Unternehmensname}` | **_Unternehmensname_** | Name des betreuenden Unternehmens                                  |
| `\def\myCompanyAddressStreet{Unternehmen Anschrift}` | **_Unternehmen Anschrift_** | Straße Hausnummer Unternehmenssitzes                                 |
| `\def\myCompanyAddressCity{Stadt des Unternehmenssitzes}` | **_Stadt des Unternehmenssitzes_** | PLZ Stadt Unternehmenssitzes                                   |

##### Projektdokumentation
Bei Projektdokumentationen gibt es die Besonderheit, dass es mehrere Autoren geben kann.
Daher wird das Feld: `\myAutor` anders belegt.

| Befehl                              | variable              | Erläuterung                                           |
| ----------------------------------- |:---------------------:| ----------------------------------------------------- |
| `\def\myType{3}`                    | **_3_**               | Option **3** ist Projektdokumentation                 |
| `\def\myAutor{Autorenliste}`        | **_Autorenliste_**    | Eine kommagetrennte Liste der Autoren, Name Nachname Martrikelnummer |

Beispiel:

```TeX
\def\myAutor{
	 Klaus Mustermann 2312354,
	 John Doe 6386782,
	 Herbert Hirnriss 50082145,
	 Peter Silie 6102134,
	 Peter Pan 3421540
	}
```
### Strukturierung der Arbeit
Es empfiehlt sich pro Kapitel eine neue Datei anzulegen.

### Verzeichnisse
TBD

### Literaturarbeit
Für die Erstellung des Literaturverzeichnises empfiehlt sich die Verwendung von:
- JabRef (http://jabref.sourceforge.net).
- Mendeley (https://www.mendeley.com/).

Die Datei ist unter ```./literatur/literatur.bib``` zu speichern.                                        

## Wichtige Befehle
TBD

## Versionierung und Backup
Es empfielt sich für das Schreiben von wissenschaftlichen Arbeiten eine Versionierung wie git zu verwenden.
Falls dies nicht möglich ist (bspw. weil man nicht bereit is für private repositories zu bezahlen), dann sollte man zumindest eine andere form des automatischen Backups verwenden.
Dazu empfehlen sich folgende lösungen:
  - Dropbox (2GB Kostenlos):
    https://www.dropbox.com/
  - Google Drive (15 GB Kostenlos):
    https://www.google.com/drive/
  - Microsoft OneDrive (Kostenpflichtig):
    https://onedrive.live.com/about/en-us/

Um einen dieser Clouddienste zu benutzen, muss sich das Projektverzeichnis in dem Verzeichnis des jeweiligen Anbieters befinden.

## License
The MIT License (MIT)
Copyright (c) 2016 Julian Beisenkötter

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

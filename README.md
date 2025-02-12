# Terraform React S3 Website

Dieses Projekt enthält eine Terraform-Konfiguration, die eine statische React-App in einem AWS S3-Bucket bereitstellt. Es richtet auch die erforderlichen S3-Bucket-Einstellungen ein, damit die React-App über eine Website-URL zugänglich ist.

## Voraussetzungen

Bevor du mit diesem Projekt fortfährst, stelle sicher, dass du die folgenden Tools installiert hast:

- [Terraform](https://www.terraform.io/downloads.html) - zur Bereitstellung der AWS-Infrastruktur.
- [AWS CLI](https://aws.amazon.com/cli/) - um deine AWS-Anmeldeinformationen zu verwalten.
- [AWS-Konto](https://aws.amazon.com/) - für die Bereitstellung der Ressourcen in AWS.
- Eine [React-App](https://reactjs.org/) - der Quellcode deiner React-Anwendung, die du auf S3 bereitstellen möchtest.

## Projektstruktur

terraform-react-s3/ │ ├── terraform/ │ ├── main.tf # Terraform-Konfigurationsdatei für S3 und Website-Setup │ ├── terraform.tfvars # Terraform-Variablen für Region und Bucketname │ ├── README.md # Diese Datei │ └── react-app/ └── build/ # Der Ordner mit den kompilierten React-App-Dateien (wird nach dem Build erstellt)

less
Kopieren
Bearbeiten

## Schritte zum Starten

### 1. AWS-Konto und CLI einrichten

- Melde dich bei deinem [AWS-Konto](https://aws.amazon.com/) an.
- Konfiguriere die AWS CLI mit deinen Anmeldeinformationen:

    ```bash
    aws configure
    ```

    Gib dabei deine AWS Access Key ID, Secret Access Key, Region und das gewünschte Ausgabeformat an.

### 2. Terraform-Variablen anpassen

Öffne die Datei `terraform.tfvars` und passe die Variablen `aws_region` und `site_name` an. Beispiel:

```hcl
aws_region = "us-east-1"
site_name  = "mein-react-bucket"
aws_region: Die Region, in der dein S3-Bucket erstellt werden soll (z. B. us-east-1).
site_name: Der Name deines S3-Buckets, der als öffentlich zugängliche Website dienen wird.
3. React-App builden
Stelle sicher, dass du die React-App gebaut hast. Wenn du die React-App noch nicht gebaut hast, gehe in das Verzeichnis der App und führe den folgenden Befehl aus:

bash
Kopieren
Bearbeiten
npm run build
Dies erstellt den Ordner build, der alle optimierten Dateien für die Produktion enthält.

4. Terraform anwenden
Führe die folgenden Terraform-Befehle aus, um die AWS-Ressourcen zu erstellen:

bash
Kopieren
Bearbeiten
cd terraform
terraform init   # Initialisiert Terraform
terraform plan   # Zeigt den Plan der Änderungen an
terraform apply  # Wendet die Änderungen an und erstellt die Ressourcen
Terraform wird nun ein S3-Bucket erstellen und deine React-App-Dateien in das Bucket hochladen.

5. Website-URL abrufen
Nachdem Terraform die Ressourcen bereitgestellt hat, findest du die URL der Website im Terraform-Ausgabewert. Beispiel:

makefile
Kopieren
Bearbeiten
Outputs:

website_url = "https://mein-react-bucket.s3-website-us-east-1.amazonaws.com"
Du kannst diese URL in deinem Browser öffnen, um deine React-App zu sehen.

Bereinigung
Wenn du das Projekt nicht mehr benötigst, kannst du alle Ressourcen mit Terraform löschen:

bash
Kopieren
Bearbeiten
terraform destroy
Dies entfernt alle in diesem Projekt erstellten AWS-Ressourcen.

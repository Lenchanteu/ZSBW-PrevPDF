# EN
# Description

This project is intended for the **Zone de Secours du Brabant wallon**. It can also be modified and adapted for other applications.

This program generates PDF files from a Word document template and data entered by the user.

# Requirements

This project uses **Python 3.13**. On Windows, **Microsoft Word** is required for PDF generation. On Linux, **LibreOffice** is required instead.

The project was developed and tested with **Python 3.13.15** and **Microsoft Word 365 — version 16.0.20326.20112**, or a compatible version. The author cannot guarantee that the application will work correctly with other versions of these programs.

A functional email address is also required.

The program was tested on **Windows 11**. A **Linux** version is also available and has been tested on Raspberry Pi OS and Ubuntu Linux.

For Linux installations, `pdf_maker.py` must use LibreOffice for PDF conversion, and `pywin32` must not be installed. **LibreOffice is required on Linux.**

# How to Use This Program

1. Download the files from GitHub and extract the ZIP archive into the installation directory.

2. Install [Python 3.13](https://www.python.org/downloads/), then open a terminal in the installation directory and run:

```bash
pip install -r requirements.txt
```

3. Configure your `.env` file using the provided `.env.example` file as a template.

4. Configure the email addresses used to send reports to municipalities in `email_config.py`.

5. Start the application:

```bash
cd Your_installation_directory
flask run
```

For production deployments, it is recommended to use a production WSGI server such as Gunicorn instead of Flask's development server.

# Technical Description

This section provides a technical description of the application. To learn how to use the program, please consult the `Your_app_name/usage` page.

1. The current application architecture is not designed for a large number of simultaneous users. In practice, it is intended for approximately **20 users generating PDF files simultaneously**.

2. A user account is required in order to store and manage generated files.

3. Generated files are stored in the application's configured data directory. On the original Windows installation, this was `C:/ProgramData/ZSBW/`.

4. An administration dashboard is available at `/admin`.

5. An email address is required to verify the identity of users and to allow them to recover or change their password.

6. This program can be adapted to generate other types of documents. This can be done by modifying `Rapport_de_prévention_incendie_template.docx` and `rapport.html` in `/templates`, while following the format used by the existing files.

   **Warning:** the variable names used in these files must be preserved exactly. If the variables are **not exactly identical**, PDF generation will **not work**.

7. For additional information or requests, please contact the author through the discussions of the GitHub repository, in the **General** category, or by email at `vancranemmerlin@gmail.com`.

# Security

This program was developed with security as one of its priorities. To help protect users, the application uses, among other measures:

- password hashing with **Argon2**;
- **CSRF** protection;
- `HttpOnly` and `SameSite=Lax` session cookies;
- file path validation to help prevent directory traversal attacks;
- mandatory authentication for accessing users' reports;
- mandatory authentication for making account modifications.

It is **strongly recommended never to share the security keys** stored in the `.env` file. These keys help protect the users and files of the application.

If you believe that one of these keys has been disclosed to an unauthorized person, please **replace it immediately**.

# GDPR

This program was developed in Belgium, within the European Union. In accordance with European Union data protection legislation, collected data is protected under the [General Data Protection Regulation (GDPR)](https://www.cnil.fr/fr/reglement-europeen-protection-donnees).

More information about the collection and processing of data can be found on the `/cookies` page.

# License

This program is **source-available**. Anyone may use, modify, and redistribute the program provided that the author is appropriately credited.

This program may not be sold without the explicit permission of the author.

[ZSBW PrevPDF](https://github.com/Lenchanteu/ZSBW-PrevPDF) © 2026 by [Merlin Van Cranem](https://github.com/Lenchanteu) is distributed under a source-available license. [More information](https://github.com/Lenchanteu/ZSBW-PrevPDF/blob/main/LICENSE.md).

# FR
# Description

Ce projet est destiné à la **Zone de Secours du Brabant wallon**. Il peut également être modifié et adapté à d'autres applications.

Ce programme permet de générer des fichiers PDF à partir d'un fichier Word et des données saisies par l'utilisateur.

# Prérequis

Ce projet utilise **Microsoft Word** et **Python 3.13.15**. Ces deux programmes sont nécessaires au bon fonctionnement de l'application.

Le projet a été dévellopé et testé avec **Python 3.13.15** et **Microsoft Word 365 — version 16.0.20326.20112**, ou une version compatible. L'auteur ne peut pas garantir le bon fonctionnement de l'application avec d'autres versions de ces programmes.

Une adresse e-mail fonctionnelle est également requise.

Le programme a été testé sur **Windows 11**. Une version pour **Linux** est également disponible, le code a été testé sur RaspberryPi OS.

Pour utiliser l'application sous Linux, veuillez modifier le fichier `pdf_maker.py` en suivant les instructions qui y sont indiquées et supprimer `pywin32` du fichier `requirements.txt`. **LibreOffice est requis sous Linux.**

# Comment utiliser ce programme

1. Téléchargez les fichiers depuis GitHub et décompressez le fichier ZIP dans le dossier d'installation.

2. Installez [Python 3.13.15](https://www.python.org/downloads/release/python-31315/), puis ouvrez un terminal dans le dossier d'installation et exécutez :

```bash
pip install -r requirements.txt
```

3. Configurez votre fichier `.env` à partir du fichier `.env.example` fourni avec le projet.

4. Configurer les adresses email pour l'envois des rapports au communes dans `email_config.py`

5. Lancez l'application :

```bash
cd Votre_dossier_dinstallation
flask run
```

# Descriptif technique

Ceci est un descriptif technique de l'application. Pour apprendre à utiliser le programme, veuillez consulter la page `Votre_nom_dapp/utilisation`.

1. L'architecture actuelle de l'application n'est pas conçue pour un grand nombre d'utilisateurs simultanés. En pratique, elle est prévue pour environ **20 utilisateurs générant simultanément des fichiers PDF**.

2. Un compte utilisateur est requis afin de stocker et gérer les fichiers générés.

3. Les fichiers générés sont accessibles dans le dossier `C:/ProgramData/ZSBW/`.

4. Un tableau d'administration est accessible à l'URL `/admin`.

5. Une adresse e-mail est requise afin de vérifier l'identité des utilisateurs et de permettre la récupération ou la modification de leur mot de passe.

6. Ce programme peut être adapté afin de générer d'autres types de fichiers. Il suffit de modifier `Rapport_de_prévention_incendie_template.docx` (avec Microsoft Word) ainsi que `rapport.html` dans `/templates`, conformément au format utilisé dans les fichiers de base.

   **Attention :** veuillez respecter précisément le nom des variables utilisées dans les fichiers. Si ces variables ne sont pas **exactement identiques**, la génération du fichier PDF **ne fonctionnera pas**.

7. Pour toute informations complémentaire ou demande, veuillez contacter l'auteur du projet via les discussions du dépôt GitHub, dans la catégorie **General**, ou par e-mail à `vancranemmerlin@gmail.com`.

# Sécurité

Ce programme a été dévellopé en faisant de la sécurité l'une de ses priorités. Afin d'assurer la sécurité des utilisateurs, l'application utilise notamment :

* le hachage des mots de passe avec **Argon2** ;
* la protection **CSRF** ;
* des cookies de session `HttpOnly` et `SameSite=Lax` ;
* la validation des chemins de fichiers afin de limiter les attaques par traversée de répertoires ;
* une authentification obligatoire pour accéder aux rapports des utilisateurs ;
* une authentification obligatoire pour toute modification d'un compte.

Il est **fortement recommandé de ne jamais partager les clés de sécurité** présentes dans le fichier `.env`. Ces clés contribuent à protéger les utilisateurs et les fichiers de l'application.

Si vous pensez que l'une de ces clés a été communiquée à une personne non autorisée, veuillez **les remplacer immédiatement**.

# RGPD

Ce programme a été dévellopé en Belgique, dans l'Union Européenne. Conformément avec les lois de l'Union Européene, les données collectées sont protégées par le [réglement général sur la protection des données](https://www.cnil.fr/fr/reglement-europeen-protection-donnees). Vous pouvez trouver plus d'infos sur la collecte et le traitement des données sur la page `/cookies`. 

# Licence

Ce programme est à code source disponible. Toute personne peut utiliser, modifier et repartager le programme à condition de créditer l'auteur de manière appropriée. Ce programme ne peut pas être vendu sans la permission explicite de l'auteur.

[ZSBW PrevPDF](https://github.com/Lenchanteu/ZSBW-PrevPDF) © 2026 par [Merlin Van Cranem](https://github.com/Lenchanteu) est sous une licence à code source disponible. [Plus d'informations](https://github.com/Lenchanteu/ZSBW-PrevPDF/LICENSE.md).

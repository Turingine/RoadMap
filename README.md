# Turingine : The Sovereign Scientific Calculator 🧮

![Build Status](https://img.shields.io/badge/build-in_progress-yellow)
![License](https://img.shields.io/badge/license-GPLv3-blue)
![Hardware](https://img.shields.io/badge/hardware-Open_Source-green)
![Platform](https://img.shields.io/badge/platform-Radxa_Cubie_A7Z-red)

> **Projet TIPE 2025/2026** - _Thème : Sobriété, Efficacité, Optimisation_

## 📜 Le Projet

**Turingine** est une initiative étudiante (MP2I/MPI) visant à restaurer la souveraineté numérique dans le domaine des calculatrices scientifiques. Face à la fermeture progressive des écosystèmes propriétaires (Numworks, TI), nous concevons une machine performante et **totalement auditable**, du PCB jusqu'au Kernel.

Notre objectif n'est pas seulement de calculer, mais d'étudier l'optimisation énergétique et logicielle sur une architecture embarquée moderne.

---

## 🏗️ Architecture Technique

Le projet repose sur une approche **[Hardware/Software](https://docs.google.com/spreadsheets/d/1M4ymWU5uOKCWL2r-G26bQkTWhOHelExH1Y2YD4XoJ-g/edit?usp=sharing)** intégrée :

### 🔌 Hardware (L'efficacité matérielle)

-   **Cœur de calcul :** Radxa Cubie A7Z (SoC Allwinner A733).
    -   Architecture **big.LITTLE** (2x Cortex-A76 + 6x Cortex-A55) pour une gestion fine de l'énergie.
    -   NPU 3 TOPS (Expérimental).
-   **[Interface](https://oshwlab.com/turingine/calculatrice) :** Clavier mécanique custom (Layout 60%) sur PCB maison.
-   **Affichage :** Écran LCD SPI.

### 🐧 Software (La sobriété logicielle)

-   **OS :** Distribution Linux Embedded Custom (Basée sur Ubuntu Linux ARM).
    -   Kernel optimisé pour le hardware Radxa.
    -   Userspace minimaliste (pas de bloatware).
-   **Moteur Mathématique :** [Giac/XCas](https://www-fourier.ujf-grenoble.fr/~parisse/giac.html) (C++) pour le calcul formel symbolique.
-   **Optimisation TIPE :**
    -   **CPU Pinning :** Allocation dynamique des processus lourds sur les cœurs P (Performance) et de l'UI sur les cœurs E (Efficacité).
    -   **Boot Time :** Objectif < 5 secondes.

---

## 🗺️ Roadmap (Feuille de Route)

### Phase 1 : Le Socle (Hiver 2025) - _En cours_ 🚧

-   [x] Sélection du hardware (Radxa Cubie A7Z).
-   [ ] **Système :** Création de l'image disque "Rootfs" Custom (Xcas, GCC, OCaml, ...).
-   [x] **Hardware :** Design du PCB v1 (Matrice clavier).
-   [ ] **Software :** Compilation et exécution de Giac en ligne de commande sur la cible.

### Phase 2 : L'Intégration (Printemps 2026) 🛠️

-   [ ] **Interface :** Développement de l'UI graphique communiquant avec XCas.
-   [ ] **Hardware :** Assemblage du prototype physique (Fabrication et conception de la coque).
-   [ ] **Système :** Scripting du démarrage automatique (Systemd service) et affichage via wayland.

### Phase 3 : L'Optimisation & TIPE (Été 2026) 🚀

-   [x] **Mesures :** Comparatifs de consommation (Joules/Calcul) vs architectures classiques.
-   [ ] **Documentation :** Rédaction du dossier technique et publication des plans finaux.

---

## 🔧 Installation & Reproduction

- [Documents](https://drive.proton.me/urls/4GS7V8XAS4#EcAJzXk4TEI0) autres ( coque, statues, ...)

### Prérequis

-   Une carte Radxa Cubie A7Z.
-   Une carte microSD (16 Go min).
-   Un PC Linux pour la compilation croisée.

### Flasher l'OS (Méthode "Injection")

1.  Cloner ce dépôt.
2.  Lancer le script de construction de l'image (nécessite `qemu-user-static`) :
    ```bash
    sudo ./scripts/build_os.sh
    ```
3.  Flasher l'image générée sur la carte SD :
    ```bash
    sudo dd if=output/turingine_v1.img of=/dev/sdX bs=4M status=progress
    ```

---

## 👥 L'Équipe

-   **Nathanaël Buendia (Poitiers)** : CPGE MP2I
-   **Kamil Leys (Tours)** : CPGE MP2I

---

## ⚖️ Licence

-   **Code source :** GPLv3 (Garantit que le projet restera toujours ouvert).
-   **Hardware (PCB) :** CERN-OHL-W (Open Hardware Licence).

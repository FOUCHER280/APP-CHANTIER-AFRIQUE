# 📋 CARNET DE PROJET - APP CHANTIER AFRIQUE
Date de création : 16-07-2026

## 🎯 OBJECTIF
Créer une application Python avec 10 MODULES DONT 1 POUR FUTURES APPLICATIONS modules pour gérer chantiers TP en Afrique de l'Ouest

## 📦 STRUCTURE ACTUELLE
APP-CHANTIER/
├── main.py              (À CRÉER)
├── requirements.txt     (À CRÉER)
├── config/
│   └── config.py        (À CRÉER)
├── modules/
│   ├── module1.py       (MODULE 1 - EN COURS)
│   ├── module2.py       (MODULE 2 - EN COURS)
│   ├── module3.py       (À FAIRE)
│   ├── module4.py       (À FAIRE)
│   ├── module5.py       (À FAIRE)
│   └── module6.py       (À FAIRE)
└── assets/
    └── icones/          (À CRÉER)

## ✅ FAIT (Fin de session 16-07-2026)
- ✅ VS Code installé et configuré
- ✅ Python 3.x installé
- ✅ Structure dossiers créée
- ✅ Dossier modules/ créé
- ✅ Début Module 1 & 2 (code brut)

## ⏳ À FAIRE DEMAIN (17-07-2026)
1. Code complet Module 1 (présenté par IA)
2. Code complet Module 2 (présenté par IA)
3. Créer main.py pour appeler Module 1 et 2
4. Tester fenêtres (vérifier que ça s'ouvre)
5. Si OK → Passer à Module 3

## 🔴 BLOCAGES / BUGS
(À remplir si erreurs)

## 📝 NOTES
- Carnet mis à jour : 16-07-2026 23h50<img width="930" height="843" alt="image" src="https://github.com/user-attachments/assets/f72af4ab-9cf0-4f88-a575-b1637356b6e3" />
# -*- coding: utf-8 -*-
import tkinter as tk
from tkinter import ttk, messagebox
import sys
from pathlib import Path

sys.path.insert(0, str(Path(__file__).parent.parent))

class InterfacePrincipale:
    def __init__(self, root):
        self.root = root
        self.root.title("GESTION GLOBALE CHANTIER")
        self.root.geometry("1400x950")
        self.root.resizable(False, False)
        self.root.configure(bg="#FFFFFF")

        self.configurer_style()
        self.creer_interface()

    def configurer_style(self):
        """Configure le theme de l'application"""
        style = ttk.Style()
        style.theme_use('clam')

        style.configure('TLabel', background="#FFFFFF", font=("Arial", 10))
        style.configure('Title.TLabel', font=("Arial", 20, "bold"))
        style.configure('Header.TLabel', font=("Arial", 13), background="#FFFFFF")

    def creer_interface(self):
        """Interface accueil avec 10 modules en grille 5x2 - PLUS PETITS"""

        # ===== HEADER =====
        header = tk.Frame(self.root, bg="#F5F5F5", height=85)
        header.pack(fill=tk.X, padx=0, pady=0)
        header.pack_propagate(False)

        ttk.Label(
            header, 
            text="GESTION GLOBALE CHANTIER", 
            font=("Arial", 20, "bold"), 
            background="#F5F5F5", 
            foreground="#333333"
        ).pack(pady=(8, 3))

        ttk.Label(
            header,
            text="Selectionnez un module pour gerer votre chantier",
            font=("Arial", 9),
            background="#F5F5F5",
            foreground="#666666"
        ).pack(pady=(0, 10))

        # ===== CONTAINER MODULES =====
        container = tk.Frame(self.root, bg="#FFFFFF")
        container.pack(fill=tk.BOTH, expand=True, padx=15, pady=15)

        # Configure les colonnes et lignes FIXES
        for i in range(5):
            container.grid_rowconfigure(i, weight=1, uniform="row")
        for i in range(2):
            container.grid_columnconfigure(i, weight=1, uniform="col")

        modules = [
            {
                "num": 1,
                "logo": "⚙",
                "titre": "Initialisation",
                "sous_titre": "Affaire",
                "couleur": "#FFE4E1"
            },
            {
                "num": 2,
                "logo": "📚",
                "titre": "Bibliotheque",
                "sous_titre": "Ressources",
                "couleur": "#E1F5FE"
            },
            {
                "num": 3,
                "logo": "📋",
                "titre": "Bordereaux",
                "sous_titre": "Quantitatif - Sous-details",
                "couleur": "#E8F5E9"
            },
            {
                "num": 4,
                "logo": "📊",
                "titre": "Rapports",
                "sous_titre": "Valorisation - Editions",
                "couleur": "#FFF3E0"
            },
            {
                "num": 5,
                "logo": "💰",
                "titre": "Budgetisation",
                "sous_titre": "Budget Chantier",
                "couleur": "#FCE4EC"
            },
            {
                "num": 6,
                "logo": "✓",
                "titre": "Suivi",
                "sous_titre": "Chantier",
                "couleur": "#F3E5F5"
            },
            {
                "num": 7,
                "logo": "🔍",
                "titre": "Controle",
                "sous_titre": "Budgetaire",
                "couleur": "#E0F2F1"
            },
            {
                "num": 8,
                "logo": "👥",
                "titre": "Planification",
                "sous_titre": "Equipe",
                "couleur": "#FFF9C4"
            },
            {
                "num": 9,
                "logo": "✅",
                "titre": "Qualite",
                "sous_titre": "Conformite",
                "couleur": "#C8E6C9"
            },
            {
                "num": 10,
                "logo": "📝",
                "titre": "Integration",
                "sous_titre": "Futures",
                "couleur": "#ECEFF1"
            }
        ]

        for idx, module in enumerate(modules):
            row = idx // 2
            col = idx % 2
            self.creer_module(container, module, row, col)

        # ===== FOOTER =====
        footer = tk.Frame(self.root, bg="#F5F5F5", height=40)
        footer.pack(fill=tk.X, padx=0, pady=0, side=tk.BOTTOM)
        footer.pack_propagate(False)

        ttk.Label(
            footer,
            text="Createur : Alain Foucher",
            font=("Arial", 8),
            background="#F5F5F5",
            foreground="#999999"
        ).pack(pady=(8, 0))

    def creer_module(self, parent, module, row, col):
        """Cree une case module PLUS PETITE 220x220 - avec surbrillance complete"""
        num = module["num"]
        titre = module["titre"]
        couleur = module["couleur"]
        couleur_hover = self.assombrir_couleur(couleur)

        # Frame PRINCIPAL - REDUIT A 220x220
        frame = tk.Frame(
            parent,
            bg=couleur,
            relief=tk.SOLID,
            borderwidth=1,
            cursor="hand2",
            highlightthickness=0,
            width=220,
            height=220
        )
        frame.grid(row=row, column=col, padx=8, pady=8, sticky="nsew")
        frame.grid_propagate(False)

        # Inner frame pour padding
        inner = tk.Frame(frame, bg=couleur)
        inner.pack(fill=tk.BOTH, expand=True, padx=6, pady=6)

        # Logo
        logo_label = tk.Label(
            inner,
            text=module["logo"],
            font=("Arial", 24),
            bg=couleur,
            fg="#333333"
        )
        logo_label.pack(pady=(3, 1))

        # Titre
        titre_label = tk.Label(
            inner,
            text=titre,
            font=("Arial", 10, "bold"),
            bg=couleur,
            fg="#333333",
            wraplength=180,
            justify=tk.CENTER
        )
        titre_label.pack(pady=(0, 1))

        # Sous-titre
        sous_titre_label = tk.Label(
            inner,
            text=module["sous_titre"],
            font=("Arial", 7),
            bg=couleur,
            fg="#666666",
            wraplength=180,
            justify=tk.CENTER
        )
        sous_titre_label.pack(pady=(0, 4))

        # Separateur
        sep = tk.Frame(inner, bg="#CCCCCC", height=1)
        sep.pack(fill=tk.X, pady=(0, 4))

        # Bouton
        btn = tk.Button(
            inner,
            text=f"Module {num}",
            command=lambda: self.ouvrir_module(num, titre),
            font=("Arial", 7, "bold"),
            bg="#333333",
            fg="#FFFFFF",
            activebackground="#555555",
            activeforeground="#FFFFFF",
            relief=tk.FLAT,
            padx=6,
            pady=3,
            cursor="hand2"
        )
        btn.pack(pady=(0, 1))

        # ===== FONCTION HOVER =====
        def on_enter(event):
            frame.configure(bg=couleur_hover, relief=tk.SUNKEN, borderwidth=2)
            inner.configure(bg=couleur_hover)
            logo_label.configure(bg=couleur_hover)
            titre_label.configure(bg=couleur_hover)
            sous_titre_label.configure(bg=couleur_hover)
            sep.configure(bg="#999999")
            btn.configure(bg="#555555")

        def on_leave(event):
            frame.configure(bg=couleur, relief=tk.SOLID, borderwidth=1)
            inner.configure(bg=couleur)
            logo_label.configure(bg=couleur)
            titre_label.configure(bg=couleur)
            sous_titre_label.configure(bg=couleur)
            sep.configure(bg="#CCCCCC")
            btn.configure(bg="#333333")

        # Bind sur TOUT
        frame.bind("<Enter>", on_enter)
        frame.bind("<Leave>", on_leave)
        inner.bind("<Enter>", on_enter)
        inner.bind("<Leave>", on_leave)
        logo_label.bind("<Enter>", on_enter)
        logo_label.bind("<Leave>", on_leave)
        titre_label.bind("<Enter>", on_enter)
        titre_label.bind("<Leave>", on_leave)
        sous_titre_label.bind("<Enter>", on_enter)
        sous_titre_label.bind("<Leave>", on_leave)
        btn.bind("<Enter>", on_enter)
        btn.bind("<Leave>", on_leave)

    def assombrir_couleur(self, couleur_hex):
        """Assombrit une couleur hex"""
        couleur_hex = couleur_hex.lstrip('#')
        r, g, b = int(couleur_hex[0:2], 16), int(couleur_hex[2:4], 16), int(couleur_hex[4:6], 16)
        r = max(0, r - 30)
        g = max(0, g - 30)
        b = max(0, b - 30)
        return f"#{r:02x}{g:02x}{b:02x}"

    def ouvrir_module(self, num_module, titre_module):
        """Ouvre le module selectionne"""

        if num_module == 1:
            try:
                print("🔍 Tentative import Module1...")
                from app.gui.module_1_initialisation import Module1
                print(f"✅ Module1 importé avec succès")
                self.ouvrir_fenetre_module(Module1, f"Module {num_module} - {titre_module}")
            except ImportError as e:
                print(f"❌ ERREUR IMPORT : {str(e)}")
                messagebox.showerror("ERREUR IMPORT", f"Impossible d'importer Module {num_module}\n{str(e)}")
            except Exception as e:
                print(f"❌ ERREUR GENERALE : {str(e)}")
                messagebox.showerror("ERREUR", f"Impossible d'ouvrir Module {num_module}\n{str(e)}")

        elif num_module == 2:
            try:
                print("🔍 Tentative import Module2...")
                from app.gui.module_2_bibliotheque_gui import Module2
                print(f"✅ Module2 importé avec succès")
                self.ouvrir_fenetre_module(Module2, f"Module {num_module} - {titre_module}")
            except ImportError as e:
                print(f"❌ ERREUR IMPORT : {str(e)}")
                messagebox.showerror("ERREUR IMPORT", f"Impossible d'importer Module {num_module}\n{str(e)}")
            except Exception as e:
                print(f"❌ ERREUR GENERALE : {str(e)}")
                messagebox.showerror("ERREUR", f"Impossible d'ouvrir Module {num_module}\n{str(e)}")

        else:
            messagebox.showinfo("PROCHAINEMENT", f"Module {num_module} - {titre_module}\n\nSera disponible tres bientot !")

    def ouvrir_fenetre_module(self, classe_module, titre):
        """Ouvre une nouvelle fenetre pour le module"""
        window = tk.Toplevel(self.root)
        window.title(titre)
        window.geometry("1100x700")
        window.configure(bg="#FFFFFF")
        app = classe_module(window)

if __name__ == "__main__":
    root = tk.Tk()
    app = InterfacePrincipale(root)
    root.mainloop()

    INTERFACE DEJA VALIDEE QUAND ON OUVRE L APPLICATION
# -*- coding: utf-8 -*-
import tkinter as tk
from tkinter import ttk, messagebox
import sys
from pathlib import Path

sys.path.insert(0, str(Path(__file__).parent.parent))

class InterfacePrincipale:
    def __init__(self, root):
        self.root = root
        self.root.title("GESTION GLOBALE CHANTIER")
        self.root.geometry("1400x950")
        self.root.resizable(False, False)
        self.root.configure(bg="#FFFFFF")

        self.configurer_style()
        self.creer_interface()

    def configurer_style(self):
        """Configure le theme de l'application"""
        style = ttk.Style()
        style.theme_use('clam')

        style.configure('TLabel', background="#FFFFFF", font=("Arial", 10))
        style.configure('Title.TLabel', font=("Arial", 20, "bold"))
        style.configure('Header.TLabel', font=("Arial", 13), background="#FFFFFF")

    def creer_interface(self):
        """Interface accueil avec 10 modules en grille 5x2 - PLUS PETITS"""

        # ===== HEADER =====
        header = tk.Frame(self.root, bg="#F5F5F5", height=85)
        header.pack(fill=tk.X, padx=0, pady=0)
        header.pack_propagate(False)

        ttk.Label(
            header, 
            text="GESTION GLOBALE CHANTIER", 
            font=("Arial", 20, "bold"), 
            background="#F5F5F5", 
            foreground="#333333"
        ).pack(pady=(8, 3))

        ttk.Label(
            header,
            text="Selectionnez un module pour gerer votre chantier",
            font=("Arial", 9),
            background="#F5F5F5",
            foreground="#666666"
        ).pack(pady=(0, 10))

        # ===== CONTAINER MODULES =====
        container = tk.Frame(self.root, bg="#FFFFFF")
        container.pack(fill=tk.BOTH, expand=True, padx=15, pady=15)

        # Configure les colonnes et lignes FIXES
        for i in range(5):
            container.grid_rowconfigure(i, weight=1, uniform="row")
        for i in range(2):
            container.grid_columnconfigure(i, weight=1, uniform="col")

        modules = [
            {
                "num": 1,
                "logo": "⚙",
                "titre": "Initialisation",
                "sous_titre": "Affaire",
                "couleur": "#FFE4E1"
            },
            {
                "num": 2,
                "logo": "📚",
                "titre": "Bibliotheque",
                "sous_titre": "Ressources",
                "couleur": "#E1F5FE"
            },
            {
                "num": 3,
                "logo": "📋",
                "titre": "Bordereaux",
                "sous_titre": "Quantitatif - Sous-details",
                "couleur": "#E8F5E9"
            },
            {
                "num": 4,
                "logo": "📊",
                "titre": "Rapports",
                "sous_titre": "Valorisation - Editions",
                "couleur": "#FFF3E0"
            },
            {
                "num": 5,
                "logo": "💰",
                "titre": "Budgetisation",
                "sous_titre": "Budget Chantier",
                "couleur": "#FCE4EC"
            },
            {
                "num": 6,
                "logo": "✓",
                "titre": "Suivi",
                "sous_titre": "Chantier",
                "couleur": "#F3E5F5"
            },
            {
                "num": 7,
                "logo": "🔍",
                "titre": "Controle",
                "sous_titre": "Budgetaire",
                "couleur": "#E0F2F1"
            },
            {
                "num": 8,
                "logo": "👥",
                "titre": "Planification",
                "sous_titre": "Equipe",
                "couleur": "#FFF9C4"
            },
            {
                "num": 9,
                "logo": "✅",
                "titre": "Qualite",
                "sous_titre": "Conformite",
                "couleur": "#C8E6C9"
            },
            {
                "num": 10,
                "logo": "📝",
                "titre": "Integration",
                "sous_titre": "Futures",
                "couleur": "#ECEFF1"
            }
        ]

        for idx, module in enumerate(modules):
            row = idx // 2
            col = idx % 2
            self.creer_module(container, module, row, col)

        # ===== FOOTER =====
        footer = tk.Frame(self.root, bg="#F5F5F5", height=40)
        footer.pack(fill=tk.X, padx=0, pady=0, side=tk.BOTTOM)
        footer.pack_propagate(False)

        ttk.Label(
            footer,
            text="Createur : Alain Foucher",
            font=("Arial", 8),
            background="#F5F5F5",
            foreground="#999999"
        ).pack(pady=(8, 0))

    def creer_module(self, parent, module, row, col):
        """Cree une case module PLUS PETITE 220x220 - avec surbrillance complete"""
        num = module["num"]
        titre = module["titre"]
        couleur = module["couleur"]
        couleur_hover = self.assombrir_couleur(couleur)

        # Frame PRINCIPAL - REDUIT A 220x220
        frame = tk.Frame(
            parent,
            bg=couleur,
            relief=tk.SOLID,
            borderwidth=1,
            cursor="hand2",
            highlightthickness=0,
            width=220,
            height=220
        )
        frame.grid(row=row, column=col, padx=8, pady=8, sticky="nsew")
        frame.grid_propagate(False)

        # Inner frame pour padding
        inner = tk.Frame(frame, bg=couleur)
        inner.pack(fill=tk.BOTH, expand=True, padx=6, pady=6)

        # Logo
        logo_label = tk.Label(
            inner,
            text=module["logo"],
            font=("Arial", 24),
            bg=couleur,
            fg="#333333"
        )
        logo_label.pack(pady=(3, 1))

        # Titre
        titre_label = tk.Label(
            inner,
            text=titre,
            font=("Arial", 10, "bold"),
            bg=couleur,
            fg="#333333",
            wraplength=180,
            justify=tk.CENTER
        )
        titre_label.pack(pady=(0, 1))

        # Sous-titre
        sous_titre_label = tk.Label(
            inner,
            text=module["sous_titre"],
            font=("Arial", 7),
            bg=couleur,
            fg="#666666",
            wraplength=180,
            justify=tk.CENTER
        )
        sous_titre_label.pack(pady=(0, 4))

        # Separateur
        sep = tk.Frame(inner, bg="#CCCCCC", height=1)
        sep.pack(fill=tk.X, pady=(0, 4))

        # Bouton
        btn = tk.Button(
            inner,
            text=f"Module {num}",
            command=lambda: self.ouvrir_module(num, titre),
            font=("Arial", 7, "bold"),
            bg="#333333",
            fg="#FFFFFF",
            activebackground="#555555",
            activeforeground="#FFFFFF",
            relief=tk.FLAT,
            padx=6,
            pady=3,
            cursor="hand2"
        )
        btn.pack(pady=(0, 1))

        # ===== FONCTION HOVER =====
        def on_enter(event):
            frame.configure(bg=couleur_hover, relief=tk.SUNKEN, borderwidth=2)
            inner.configure(bg=couleur_hover)
            logo_label.configure(bg=couleur_hover)
            titre_label.configure(bg=couleur_hover)
            sous_titre_label.configure(bg=couleur_hover)
            sep.configure(bg="#999999")
            btn.configure(bg="#555555")

        def on_leave(event):
            frame.configure(bg=couleur, relief=tk.SOLID, borderwidth=1)
            inner.configure(bg=couleur)
            logo_label.configure(bg=couleur)
            titre_label.configure(bg=couleur)
            sous_titre_label.configure(bg=couleur)
            sep.configure(bg="#CCCCCC")
            btn.configure(bg="#333333")

        # Bind sur TOUT
        frame.bind("<Enter>", on_enter)
        frame.bind("<Leave>", on_leave)
        inner.bind("<Enter>", on_enter)
        inner.bind("<Leave>", on_leave)
        logo_label.bind("<Enter>", on_enter)
        logo_label.bind("<Leave>", on_leave)
        titre_label.bind("<Enter>", on_enter)
        titre_label.bind("<Leave>", on_leave)
        sous_titre_label.bind("<Enter>", on_enter)
        sous_titre_label.bind("<Leave>", on_leave)
        btn.bind("<Enter>", on_enter)
        btn.bind("<Leave>", on_leave)

    def assombrir_couleur(self, couleur_hex):
        """Assombrit une couleur hex"""
        couleur_hex = couleur_hex.lstrip('#')
        r, g, b = int(couleur_hex[0:2], 16), int(couleur_hex[2:4], 16), int(couleur_hex[4:6], 16)
        r = max(0, r - 30)
        g = max(0, g - 30)
        b = max(0, b - 30)
        return f"#{r:02x}{g:02x}{b:02x}"

    def ouvrir_module(self, num_module, titre_module):
        """Ouvre le module selectionne"""

        if num_module == 1:
            try:
                print("🔍 Tentative import Module1...")
                from app.gui.module_1_initialisation import Module1
                print(f"✅ Module1 importé avec succès")
                self.ouvrir_fenetre_module(Module1, f"Module {num_module} - {titre_module}")
            except ImportError as e:
                print(f"❌ ERREUR IMPORT : {str(e)}")
                messagebox.showerror("ERREUR IMPORT", f"Impossible d'importer Module {num_module}\n{str(e)}")
            except Exception as e:
                print(f"❌ ERREUR GENERALE : {str(e)}")
                messagebox.showerror("ERREUR", f"Impossible d'ouvrir Module {num_module}\n{str(e)}")

        elif num_module == 2:
            try:
                print("🔍 Tentative import Module2...")
                from app.gui.module_2_bibliotheque_gui import Module2
                print(f"✅ Module2 importé avec succès")
                self.ouvrir_fenetre_module(Module2, f"Module {num_module} - {titre_module}")
            except ImportError as e:
                print(f"❌ ERREUR IMPORT : {str(e)}")
                messagebox.showerror("ERREUR IMPORT", f"Impossible d'importer Module {num_module}\n{str(e)}")
            except Exception as e:
                print(f"❌ ERREUR GENERALE : {str(e)}")
                messagebox.showerror("ERREUR", f"Impossible d'ouvrir Module {num_module}\n{str(e)}")

        else:
            messagebox.showinfo("PROCHAINEMENT", f"Module {num_module} - {titre_module}\n\nSera disponible tres bientot !")

    def ouvrir_fenetre_module(self, classe_module, titre):
        """Ouvre une nouvelle fenetre pour le module"""
        window = tk.Toplevel(self.root)
        window.title(titre)
        window.geometry("1100x700")
        window.configure(bg="#FFFFFF")
        app = classe_module(window)

if __name__ == "__main__":
    root = tk.Tk()
    app = InterfacePrincipale(root)
    root.mainloop()

<img width="1392" height="978" alt="image" src="https://github.com/user-attachments/assets/bf5d90e8-a23f-44d9-9981-c8a16d5cf163" />

    ON EST ARRIVE LA HIER MAINTENANT IL FAUT QUE L ON DEVELO¨PPR MODULE  ET 2

    EN ATTENDANT, voici l'ARBORESCENCE COMPLÈTE à créer :
📦 RACINE_PROJET/
│
├── 📁 module_1/                          ← Dossier Module 1
│   ├── 📄 __init__.py                    ← (vide ou imports)
│   ├── 📄 ui_module1.py                  ← Ton interface Tkinter
│   ├── 📄 gestionnaire_affaires.py       ← LA CLASSE À CRÉER ⭐
│   └── 📁 affaires_data/                 ← DOSSIER (créé auto)
│       ├── 📄 index.json                 ← Index des affaires
│       ├── 📄 affaire_2024-001.json
│       ├── 📄 affaire_2024-002.json
│       └── 📄 affaire_2024-003.json
│
├── 📁 module_2/                          ← Ressources (à faire)
│   ├── 📄 __init__.py
│   └── 📄 ui_module2.py
│
├── 📁 module_3/                          ← Budget (à faire)
│   ├── 📄 __init__.py
│   └── 📄 ui_module3.py
│
├── 📄 main.py                            ← Lance toute l'appli
└── 📄 config.py                          ← Configuration générale
 TU M ASQ FAIT CREER CA

 VÉRIFICATION FINALE 🎯
app/gui/
  ├── dialogs/                          ✅ CRÉÉ
  │   ├── __init__.py                   ✅
  │   ├── dialog_creation_affaire.py    ✅
  │   ├── dialog_duplication_affaire.py ✅
  │   └── dialog_export_affaire.py      ✅
  ├── widgets/                          ✅
  │   ├── __init__.py                   ✅
  │   └── widget_liste_affaires.py      ✅
  ├── __init__.py                       ✅
  ├── interface_principale.py           ✅
  ├── module_1_initialisation.py        ✅
  └── module_2_bibliotheque_gui.py      ✅

app/services/                           ✅
  ├── __init__.py                       ✅
  ├── affaire_service.py                ✅
  ├── backup_manager.py                 ✅
  ├── countries_manager.py              ✅
  ├── database_manager.py               ✅
  ├── duplication_service.py            ✅
  └── session_manager.py                ✅

utils/                                  ✅
  ├── __init__.py                       ✅
  ├── converters.py                     ✅
  ├── files_manager.py                  ✅
  ├── generators.py                     ✅
  └── validators.py                     ✅
     ET CA

     FENÊTRE CRÉATION AFFAIRE (SIMPLIFIÉE) 📝
┌──────────────────────────────────────────────────┐
│  ➕ NOUVELLE AFFAIRE                             │
├──────────────────────────────────────────────────┤
│                                                   │
│  📌 IDENTIFICATION                               │
│  ┌──────────────────────────────────────────┐  │
│  │ Nom affaire *              [___________] │  │
│  │ Code affaire (Auto)        [2026-ACC-001]│  │
│  │ Pays (3 lettres) *         [ACC]         │  │
│  │ Zone géographique *        [___________] │  │
│  │ Localisation *             [___________] │  │
│  └──────────────────────────────────────────┘  │
│                                                   │
│  👥 INTERVENANTS                                │
│  ┌──────────────────────────────────────────┐  │
│  │ Client *                   [___________] │  │
│  │ Maitre d'ouvrage *         [___________] │  │
│  │ Maitre d'œuvre             [___________] │  │
│  │ Responsable chantier       [___________] │  │
│  │ Contact chantier           [___________] │  │
│  └──────────────────────────────────────────┘  │
│                                                   │
│  💰 FINANCIER                                   │
│  ┌──────────────────────────────────────────┐  │
│  │ Budget total (FCFA) *      [___________] │  │
│  │ Devise principale *        [FCFA ▼]     │  │
│  │ Deuxième devise (opt)      [EURO ▼]     │  │
│  │ Taux change                [650 FCFA/€] │  │
│  │ Inflation prévue (%)       [2.5%]       │  │
│  │ Contingence (%)            [5%]         │  │
│  └──────────────────────────────────────────┘  │
│                                                   │
│  📅 CALENDRIER & GÉOMÉTRIE                      │
│  ┌──────────────────────────────────────────┐  │
│  │ Date début *               [16/07/2026]  │  │
│  │ Date fin prévue *          [15/12/2026]  │  │
│  │ Longueur du projet (km)    [25.5]       │  │
│  │ (Optionnel)                              │  │
│  └──────────────────────────────────────────┘  │
│                                                   │
│  📝 NOTES & OBSERVATIONS                        │
│  ┌──────────────────────────────────────────┐  │
│  │ [____________________________]            │  │
│  │ [____________________________]            │  │
│  │ (Explications complémentaires si besoin) │  │
│  └──────────────────────────────────────────┘  │
│                                                   │
│  [ ✅ CRÉER ]  [ ❌ ANNULER ]                  │
└──────────────────────────────────────────────────┘ STRUCTURE MODULE 1

# 🌌 Grok : Générateur de suggestions, scripts, scènes et automatisation

![Logo](https://raw.githubusercontent.com/XAV59213/grok_automation_suggester/main/images/Grok-Logo-Text-512x256.png)

[![GitHub release](https://img.shields.io/github/v/release/XAV59213/grok_automation_suggester)](https://github.com/XAV59213/grok_automation_suggester/releases)
[![Downloads](https://img.shields.io/github/downloads/XAV59213/grok_automation_suggester/total.svg?label=Downloads)](https://github.com/XAV59213/grok_automation_suggester/releases)
[![HACS Custom](https://img.shields.io/badge/HACS-Custom-orange.svg?logo=home-assistant)](https://hacs.xyz/)

<a href="https://www.buymeacoffee.com/xav59213">
  <img src="https://img.buymeacoffee.com/button-api/?text=xav59213&emoji=&slug=xav59213&button_colour=5F7FFF&font_colour=ffffff&font_family=Cookie&outline_colour=000000&coffee_colour=FFDD00" />
</a>

---

## 🚀 Présentation

**Grok Automation Suggester** est une intégration Home Assistant propulsée par l’IA **Grok** de **xAI**, conçue pour générer automatiquement des suggestions d’automatisations **intelligentes** et **fun**. Inspirée par *Le Guide du voyageur galactique* et *JARVIS*, elle transforme votre maison connectée en vaisseau spatial intelligent 🛸.

---

## ✨ Fonctionnalités

- 🤖 **Suggestions IA** : Génère des automations en fonction de vos entités, zones et appareils.
- 🌌 **Style Grok** : Prompts humoristiques et vibe intergalactique.
- 🔔 **Notifications persistantes** dans Home Assistant.
- 📊 **Capteurs intégrés** :  
  - `sensor.grok_automation_suggestions`  
  - `sensor.grok_automation_status`
- ⚙️ **Configuration simple** via l’UI de Home Assistant.
- 💬 **Prompt personnalisé** pour guider les suggestions.

---

## 🛠️ Installation

### 📦 Via HACS

1. Ajoutez ce dépôt comme **Custom Repository** :  
   `https://github.com/XAV59213/grok_automation_suggester`
2. Recherchez **Grok Automation Suggester** et installez.
3. Redémarrez Home Assistant.

### 📁 Manuelle

1. Copiez le dossier `custom_components/grok_automation_suggester/` dans votre répertoire `custom_components/`.
2. Redémarrez Home Assistant.

---

## ⚙️ Configuration

1. Allez dans **Paramètres > Appareils & Services > Ajouter une intégration**.
2. Sélectionnez **Grok Automation Suggester**.
3. Entrez votre **clé API Grok** (à obtenir sur [https://console.x.ai](https://console.x.ai)).
4. Configurez les options : modèle, nombre max de tokens, etc.

---

## 🚧 Utilisation

### 🔧 Service : `grok_automation_suggester.generate_suggestions`

- `all_entities` *(bool)* : Analyse toutes les entités ou seulement les nouvelles.
- `custom_prompt` *(string, optionnel)* : Exemple — *"Crée des automatisations pour économiser l’énergie"*.

### 🧠 Automatisation d'exemple

Fichier : `grok_new_entity_automation.yaml`  
> Déclenche une suggestion quand une nouvelle entité est détectée.

### 🛰️ Capteurs disponibles

- `sensor.grok_automation_suggestions` : Contenu des suggestions.
- `sensor.grok_automation_status` : État de connexion à l’API Grok.

---

## 🔑 Obtenir une clé API

Inscrivez-vous sur [https://console.x.ai](https://console.x.ai) pour obtenir une clé d’API gratuite (ou premium).

---

## 🧪 Exemple de suggestion

> *Yo, j’ai scanné ton salon et trouvé `light.living_room_lamp` et `sensor.motion_living_room`... Voici une idée pour rendre ton salon plus cool :*

```yaml
- id: living_room_motion_light
  alias: Allumer la lampe du salon sur détection de mouvement
  description: Active la lampe quand quelqu’un entre dans le salon, mais seulement le soir.
  trigger:
    - platform: state
      entity_id: sensor.motion_living_room
      to: "on"
  condition:
    - condition: sun
      after: sunset
  action:
    - service: light.turn_on
      target:
        entity_id: light.living_room_lamp
      data:
        brightness_pct: 80
```
    Prêt à transformer ton salon en cockpit spatial ? 🚀

🤝 Contribuer

    Forkez le dépôt : https://github.com/XAV59213/grok_automation_suggester

    Apportez vos modifications.

    Soumettez une Pull Request.

    Signalez bugs & idées via les Issues.

Pour tester localement, placez le code dans custom_components/grok_automation_suggester/ puis redémarrez Home Assistant.
🙏 Remerciements

    Basé sur le projet original ai_automation_suggester

    Propulsé par xAI

    À vos automatisations, et que la force intergalactique soit avec vous ! 😎

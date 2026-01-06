<p align="center">
  <img src="https://img.shields.io/badge/System-CRAID_Distributed-blue?style=for-the-badge&logo=server" alt="System">
  <img src="https://img.shields.io/badge/Algorithm-Reed--Solomon-orange?style=for-the-badge&logo=wolframmathematica" alt="Algo">
  <img src="https://img.shields.io/badge/Resilience-Self--Healing-green?style=for-the-badge&logo=shield" alt="Resilience">
</p>

<div align="center">
  <h1>🛡️ CRAID : Cognitive RAID Architecture</h1>
  <h3>Redundant Array of Independent Datasets</h3>
  <p><em>"Memory is not a file. It is a reconstruction."</em></p>
</div>

---

## 🧠 Le Concept : Une Mémoire Holographique

Les systèmes actuels (RAG, Vector DBs) sont fragiles : si vous perdez le fichier d'index, vous perdez la mémoire.
**CRAID** applique la logique du stockage RAID matériel à la **mémoire sémantique**. Il fragmente le savoir en "éclats" mathématiques et les distribue sur le réseau.

* **Résultat :** Vous pouvez perdre **40% de vos nœuds (Agents)**, le système reconstruira mathématiquement les souvenirs manquants sans perte de données.

## ⚙️ Architecture Technique

### 1. La "Semantic Polymerase" (Ingestion) 🧬
Avant d'être stockée, l'information brute passe par un pipeline biologique (`semantic_polymerase.md`) :
1.  **Helicase (Extraction)** : Un SLM (Mistral/Phi) brise le texte en triplets *Sujet-Verbe-Objet*.
2.  **Synthèse (Embedding)** : Création d'un "Nucléotide Sémantique" (Vecteur + Sens).
3.  **Distribution** : Le nucléotide est envoyé au cluster CRAID.

### 2. Le Protocole de Sharding (Distribution) 📦
Nous utilisons un **Erasure Coding (Reed-Solomon)**.
* **Standard (3, 2)** : La donnée est coupée en 3 morceaux, et 2 blocs de parité sont calculés.
* **Répartition** : Ces 5 blocs sont envoyés à 5 agents différents.
* **Reconstruction** : Il suffit de récupérer n'importe quels 3 blocs pour régénérer le tout.

### 3. Gestion de la Mutabilité (LSM Tree) 🌳
Pour gérer l'apprentissage continu sans corrompre les shards existants :
* **Hot Memory (MemTable)** : Les souvenirs récents vivent en RAM (rapide, volatile).
* **Cold Storage (SSTables)** : Une fois stabilisés, ils sont "vitrifiés" sur le disque en shards immuables.

---

## 📐 Formules de Résilience

La robustesse du système est définie mathématiquement dans [`FORMULAS.md`](./FORMULAS.md).

**Probabilité d'échec ($P_{fail}$)** :
$$P_{fail} = \sum_{i=M+1}^{N+M} \binom{N+M}{i} p^i (1-p)^{N+M-i}$$

> Avec une configuration $(3,2)$, la probabilité de perdre un souvenir est statistiquement négligeable, même dans un environnement hostile.

---

## 📂 Contenu du Répo

| Fichier | Description |
| :--- | :--- |
| **`specs/protocol_sharding.md`** | Spécification technique du découpage Reed-Solomon. |
| **`concepts/semantic_polymerase.md`** | Architecture du pipeline d'ingestion (Helicase). |
| **`craid.md`** | Vue d'ensemble de la topologie Kuramoto. |
| **`FORMULAS.md`** | Preuves mathématiques de la résilience. |

---

> **"Un souvenir partagé est un souvenir qui ne peut pas mourir."**

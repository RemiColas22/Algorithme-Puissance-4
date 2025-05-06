# Projet Puissance 4 - IA Stratégique  
### Groupe 3 - 1D1  
Développé par Rémi Colas & Nathan Filaux  

## 🎯 Objectif  
Développer un algorithme en langage **C** capable de jouer à Puissance 4 avec :  
- Le moins de coups possible pour gagner  
- Un **temps de calcul réduit**
- Un **taux de victoire > 50%**

## 🧠 Description du projet  
Deux stratégies ont été développées : **Stratégie offensive** et **Stratégie défensive**, avec gestion intelligente des coups pour bloquer ou gagner efficacement.

---

## ⚙️ Stratégies communes  
- **Validation diagonale** : avant de compléter ou bloquer une diagonale, on vérifie si le pion est soutenu (ne tombera pas plus bas que prévu).  
- **Placement centré** : en cas de choix entre gauche ou droite, on privilégie le placement **le plus proche du centre** de la grille.

---

## 🚀 Stratégie 1 : Offensive  

### Déroulement :  
1. **Premier tour - premier joueur** → joue au **centre**.  
2. **Premier tour - deuxième joueur** → joue **collé** au pion adverse (gauche/droite) en se rapprochant du centre.  
3. **Victoire en un coup possible** → on joue le **coup gagnant**.  
4. **Menace adverse imminente (3 pions alignés)** → on **bloque**.  

### Phase offensive (si l’adversaire ne peut pas gagner au prochain coup) :  
5. Si 2 pions alignés → on tente d’**enchaîner un 3e** pion (priorité au centre).  
6. Sinon → on place un pion **près d’un autre existant** (priorité : au-dessus, diagonale, verticale).  
7. Sinon → on joue dans la **colonne centrale**.

---

## 🛡️ Stratégie 2 : Défensive  

### Optimisation :  
- À chaque fin de tour, la grille est **enregistrée dans un fichier**.
- Cela permet de **réduire le temps de calcul** au prochain tour en ciblant uniquement la zone autour du dernier coup adverse.

### Déroulement :  
1. **Premier tour** :  
   - Si premier joueur → joue au **centre**.  
   - Si deuxième joueur → joue à côté du pion adverse (à droite si l’adversaire a joué au centre).  

2. Si 3 pions alignés → **complète** pour **gagner**.  
3. Si l’adversaire a 3 pions alignés → **bloque** pour l’empêcher de gagner.  

### Phase défensive :  
- On compare la grille actuelle avec la sauvegarde pour trouver le **dernier coup adverse**.  
- On analyse autour de ce pion pour **bloquer les alignements potentiels**.

### Phase offensive (si aucune menace adverse) :  
4. Si 2 pions alignés → **complète l’alignement**, en priorité celui **proche du centre**.  
5. Sinon → joue depuis le **pion le plus proche du centre**, en visant :
   - D'abord une **diagonale**
   - Puis une **ligne**
   - Enfin une **colonne**

---

## 🔧 Langage utilisé  
- **C (langage bas niveau)**  
- Manipulation directe de la grille, simulation de coups, et heuristiques simples pour prise de décision.

---

## 📈 Résultats attendus  
- Gagner plus de **50% des parties**  
- Réduction **drastique** du temps de calcul  
- Jouer de manière **intelligente** et **anticipative**


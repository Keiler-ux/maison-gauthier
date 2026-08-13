# Configuration Supabase - Partage en Temps Réel

## ✅ Qu'est-ce que vous avez obtenu

Votre site est maintenant configuré pour synchroniser **en temps réel** les événements du calendrier à travers tous les appareils et navigateurs de votre famille ! 🎉

### Fonctionnalités activées :
- ✅ **Synchronisation instantanée** - Toute modification est visible par tous immédiatement
- ✅ **Partage famille** - Tous les utilisateurs voient les mêmes événements
- ✅ **Modification partagée** - Chacun peut créer, éditer ou supprimer des événements
- ✅ **Pas de limite** - Aucune limite sur le nombre d'événements

---

## 📝 Configuration de Supabase

Vous avez déjà réalisé les étapes principales :

### 1. ✅ Compte Supabase créé
- URL du projet : `https://vycloqcfpqhmzanjmhat.supabase.co`
- Clé API : `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...` (déjà intégrée)

### 2. ✅ Table créée
Vous avez exécuté cette requête SQL dans Supabase :

```sql
CREATE TABLE events (
  id BIGINT PRIMARY KEY GENERATED ALWAYS AS IDENTITY,
  date VARCHAR(10) NOT NULL,
  end_date VARCHAR(10),
  title VARCHAR(255) NOT NULL,
  author VARCHAR(255),
  start_time VARCHAR(5),
  end_time VARCHAR(5),
  type VARCHAR(50) DEFAULT 'default',
  description TEXT,
  all_day BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);
```

### 3. ✅ Code intégré
Les fichiers suivants ont été mis à jour :
- `agenda.html` - Calendrier connecté à Supabase
- `index.html` - Page d'accueil affichant les événements à venir

---

## 🚀 Tester la synchronisation

### Étape 1 : Ajouter un événement de test

1. Ouvrez https://maison-gauthier.vercel.app/agenda
2. Cliquez sur "+ Ajouter un événement"
3. Remplissez les champs :
   - **Titre** : "Test de sync"
   - **Auteur** : Votre nom
   - **Date** : Aujourd'hui ou demain
   - **Type** : "default"
4. Cliquez sur "Créer"

### Étape 2 : Vérifier la synchronisation

**Option A : Sur le même navigateur**
- Allez à https://maison-gauthier.vercel.app/ (page d'accueil)
- L'événement doit apparaître dans "Rendez-vous à venir" 📅

**Option B : Sur un autre appareil/navigateur**
1. Ouvrez https://maison-gauthier.vercel.app/ sur téléphone, tablette, ou autre ordinateur
2. L'événement doit être visible immédiatement
3. Modifiez-le et vérifiez que la modification apparaît partout en temps réel

### Étape 3 : Migrer les événements existants (optionnel)

Si vous aviez des événements enregistrés localement, vous pouvez les ajouter manuellement :

1. Dans Supabase, allez à **SQL Editor**
2. Exécutez cette requête pour ajouter des événements de test :

```sql
INSERT INTO events (date, title, author, start_time, type, all_day, description)
VALUES
  ('2026-08-20', 'Réunion famille', 'Marie', '14:00', 'default', FALSE, ''),
  ('2026-08-25', 'Anniversaire Claire', 'Jean', NULL, 'anniversary', TRUE, ''),
  ('2026-09-10', 'Week-end escapade', 'Pierre', NULL, 'trip', TRUE, '');
```

---

## 🔒 Sécurité et Accès

### Status actuel
- **Public** : N'importe qui avec le lien peut voir et modifier les événements
- **Pas de mot de passe** : Accès ouvert (parfait pour la famille)

### Pour augmenter la sécurité (optionnel)

Si vous voulez limiter l'accès à votre famille uniquement, vous pouvez :

1. Ajouter une **authentification simple** (email/mot de passe)
2. Configurer **RLS (Row Level Security)** dans Supabase
3. Partager un lien d'invitation privée

👉 **Pour l'instant**, le partage de lien est suffisant - tous dans votre famille auront accès complet !

---

## 🐛 Dépannage

### Les événements ne s'affichent pas
1. Ouvrez la console du navigateur (F12)
2. Vérifiez s'il y a des erreurs en rouge
3. Vérifiez que Supabase.co est accessible (pas de VPN bloquant)

### La synchronisation en temps réel ne fonctionne pas
1. Rechargez la page (Ctrl+F5)
2. Vérifiez que vous avez une connexion Internet stable
3. Essayez sur un autre navigateur

### Les anciens événements ont disparu
- Ils sont encore en localStorage sur votre ancien navigateur
- Vous pouvez les ajouter manuellement via la requête SQL ci-dessus
- Ou les importer avec un script (contactez l'aide si nécessaire)

---

## 📱 Partager avec la famille

1. Donnez simplement le lien : **https://maison-gauthier.vercel.app/**
2. Ils peuvent immédiatement :
   - ✅ Voir tous les événements
   - ✅ Ajouter leurs propres événements
   - ✅ Modifier/supprimer les événements
   - ✅ Voir les changements en temps réel

Pas besoin de compte ! Pas besoin de mot de passe ! 🎉

---

## 📊 Prochaines étapes optionnelles

1. **Ajouter des catégories** - Colors spécifiques pour les type d'événements
2. **Notifications** - Alertes pour les événements importants
3. **Photos** - Ajouter des images aux événements
4. **Commentaires** - Permettre aux utilisateurs de commenter les événements
5. **Historique** - Voir qui a créé/modifié quel événement

👉 Dites-moi si vous avez besoin de l'une de ces fonctionnalités !

---

## 🆘 Support

Si quelque chose ne fonctionne pas :
1. Vérifiez que la table `events` existe dans Supabase
2. Vérifiez les erreurs dans la console du navigateur (F12)
3. Essayez de rafraîchir la page (Ctrl+F5)
4. Testez sur un autre navigateur pour exclure les problèmes de cache

Bonne chance ! 🚀

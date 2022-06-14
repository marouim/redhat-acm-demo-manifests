# Red Hat Advanced Cluster Management notes ( NON-OFFICIEL )

Ce repository n'est pas une documentation officielle. Il est utilisé pour faire
des démonstrations, partager de l'information et garder des notes et des liens importants. 

La documentation officiel se trouve au lien suivant:
https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/2.2


### Éléments de base 

##### CRD de base pour définir application et policies

La même méthodologie est utilisée autant pour les applications que les policies. 

- Channel = Définition du Git
- Subscription = Lien entre le Channel et le Placement (sélecteur)
- PlacementRule = Sélecteur. Règle de sélection des clusters de destination


## Gestion des applications

### Reconcile

Par défaut, avec la version 2.2.2, la réconciliation est définie à Medium et donc à chaque 15 minuutes. 

Pour augmenter la vitesse de réconciliation, il suffit d'annoter le Channel comme suit. L'application héritera des paramètres. Les paramètres du channel peuvent être écrasés par ceux de la subscription. 

```
apiVersion: apps.open-cluster-management.io/v1
kind: Channel
metadata:
  name: git-channel
  namespace: sample
  annotations:
    apps.open-cluster-management.io/reconcile-rate: [ Off, Low, Medium ou High ]
```

Voir documentation: 

https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/2.2/html/manage_applications/managing-applications#managing-apps-with-git-repositories



## Gestion Securité et gouvernance

### Examples

https://github.com/open-cluster-management/policy-collection


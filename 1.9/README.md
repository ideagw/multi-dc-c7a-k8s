
These are Kubernetes 1.9.x. The only change is related to StatefulSets. They are using api version apps/v1 instead of apps/v1beta. 
Accordingly, selector is added to the spec in StatefulSet definition.

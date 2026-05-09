---
id: 20251011201928
tags: 
---

---

# namepreview jewerly dev c4 context diagram

```mermaid
C4Context
    title Namepreview Jewerly context arquitecture
    
    Person(User, "User", "El calador que hara sus letras")
    
    System_Boundary(System, "System"){
    System(NamepreviewJewerly, "NamePreviewJewerly", "Genera las plantillas de nombres para descarga")
    }
    
    Rel(User, NamepreviewJewerly, "uses")
    
```

---

## Connections:
- [[]]

---

## Questions for Further Exploration:
- Roles de usuarios
- Compra de letras
- Definir si el calador podra usar libremente los creditos de letras
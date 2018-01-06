---
title: "PDB_TYPE | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PDB_TYPE
helpviewer_keywords: PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f1c08df8cf56d81ebb22fbdf17f3d20084599b51
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="pdbtype"></a>PDB_TYPE
Эта структура указывает сведения о типа поля, взяты из PDB-символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```csharp  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 ulAppDomainID  
 Идентификатор приложения, от которого поступило символа. Это используется для уникальной идентификации экземпляра приложения.  
  
 guidModule  
 Идентификатор GUID модуля, содержащего это поле.  
  
 symid  
 Идентификатор символ, который соответствует этому полю.  
  
## <a name="remarks"></a>Примечания  
 Эта структура выводится как часть объединения в [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) структуры при `dwKind` поле `TYPE_INFO` структуры задано значение `TYPE_KIND_PDB` (значение из [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Перечисление).  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
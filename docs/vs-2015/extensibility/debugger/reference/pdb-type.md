---
title: PDB_TYPE | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3aa8a4d4484cc33fba1623f732b0168a5295b3dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49947900"
---
# <a name="pdbtype"></a>PDB_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Эта структура указывает сведения о типом поля, взятое из PDB-символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Идентификатор символ, соответствующий этому полю.  
  
## <a name="remarks"></a>Примечания  
 Эта структура является частью объединения в [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) структуры, когда `dwKind` поле `TYPE_INFO` структура присваивается `TYPE_KIND_PDB` (значение из [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Перечисление).  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)


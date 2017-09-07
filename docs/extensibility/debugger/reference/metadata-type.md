---
title: "METADATA_TYPE | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: f2fd53d0e6a0b92a3c8c7b030d503578aa9d2f98
ms.contentlocale: ru-ru
ms.lasthandoff: 09/06/2017

---
# <a name="metadatatype"></a>METADATA_TYPE
Эта структура указывает сведения о типа поля, берутся из метаданных.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```csharp  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 ulAppDomainID  
 Идентификатор приложения, от которого поступило символа. Это используется для уникальной идентификации экземпляра приложения.  
  
 guidModule  
 Идентификатор GUID модуля, содержащего это поле.  
  
 tokClass  
 Идентификатор маркера метаданных этого типа.  
  
 [C++] `_mdToken` — `typedef` для 32-разрядных `int`.  
  
## <a name="remarks"></a>Примечания  
 Эта структура выводится как часть объединения в [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) структуры при `dwKind` поле `TYPE_INFO` структуры задано значение `TYPE_KIND_METADATA` (значение из [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Перечисление).  
  
 `tokClass` Значение представляет собой лексему метаданных, который уникально определяет тип. Дополнительные сведения об интерпретации старшие разряды идентификатор маркера метаданных см. в разделе `CorTokenType` перечисления в файле corhdr.h в [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] пакета SDK.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)

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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 478cf0efe2bcb9079731ffd3154ce55352e35805
ms.lasthandoff: 02/22/2017

---
# <a name="metadatatype"></a>METADATA_TYPE
Эта структура содержит сведения о тип поля берутся из метаданных.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```c#  
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
  
 [C++] `_mdToken` is a `typedef` for a 32-bit `int`.  
  
## <a name="remarks"></a>Примечания  
 Эта структура является частью объединения в [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) структуры при `dwKind` поле `TYPE_INFO` структуры задано значение `TYPE_KIND_METADATA` (значение из [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) перечисления).  
  
 `tokClass` Значение представляет собой лексему метаданных, который уникально определяет тип. Дополнительные сведения об интерпретации старшие разряды идентификатор маркера метаданных см. в разделе `CorTokenType` перечисления в файле corhdr.h в [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] пакета SDK.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)

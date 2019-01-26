---
title: METADATA_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c276c34b902358ab355f1a67ffa1d97f4f0f8ce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034721"
---
# <a name="metadatatype"></a>METADATA_TYPE
Эта структура указывает сведения о типом поля, взятое из метаданных.  
  
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
 Эта структура является частью объединения в [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) структуры, когда `dwKind` поле `TYPE_INFO` структура присваивается `TYPE_KIND_METADATA` (значение из [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Перечисление).  
  
 `tokClass` Значение является маркером метаданных, который уникально определяет тип. Дополнительные сведения о том, как интерпретировать старшие разряды идентификатор маркера метаданных см. в разделе `CorTokenType` перечисления в файле corhdr.h в [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] пакета SDK.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
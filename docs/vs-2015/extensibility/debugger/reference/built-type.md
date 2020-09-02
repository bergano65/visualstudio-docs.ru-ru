---
title: BUILT_TYPE | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6becf886d361e203dca313a7aa1dfdf166aa4614
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153175"
---
# <a name="built_type"></a>BUILT_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Эта структура задает сведения о типе поля, взятого из метаданных.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct _tagTYPE_BUILT {  
   ULONG32      ulAppDomainID;  
   GUID         guidModule;  
   IDebugField* pUnderlyingField;  
} BUILT_TYPE;  
```  
  
```csharp  
public struct BUILT_TYPE {  
   public uint        ulAppDomainID;  
   public Guid        guidModule;  
   public IDebugField pUnderlyingField;  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 улаппдомаинид  
 Идентификатор приложения, от которого получен символ. Используется для уникальной идентификации экземпляра приложения.  
  
 гуидмодуле  
 Идентификатор GUID модуля, содержащего это поле.  
  
 пундерлингфиелд  
 Объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , определяющий базовое поле, связанное с этим построенным полем.  
  
## <a name="remarks"></a>Remarks  
 Эта структура отображается как часть объединения в структуре [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) , если `dwKind` поле `TYPE_INFO` структуры имеет `TYPE_KIND_BUILT` значение (Value из перечисления [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

---
title: DEBUG_REFERENCE_INFO | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 675373ae1728bbca2cc7a89fdaa8014e6286d8b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159327"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Описывает ссылку.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct tagDEBUG_REFERENCE_INFO {   
   DEBUGREF_INFO_FLAGS dwFields;  
   BSTR                bstrName;  
   BSTR                bstrType;  
   BSTR                bstrValue;  
   DBG_ATTRIB_FLAGS    dwAttrib;  
   REFERENCE_TYPE.     dwRefType;  
   IDebugReference2*   m_pReference;  
} DEBUG_REFERENCE_INFO;  
```  
  
```csharp  
public struct DEBUG_REFERENCE_INFO {   
   public uint             dwFields;  
   public string           bstrName;  
   public string           bstrType;  
   public string           bstrValue;  
   public ulong            dwAttrib;  
   public uint.            dwRefType;  
   public IDebugReference2 m_pReference;  
};  
```  
  
## <a name="members"></a>Участники  
 двфиелдс  
 Сочетание флагов из перечисления [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) , которое указывает, какие поля заполняются.  
  
 bstrName  
 Заданное пользователем имя объекта [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .  
  
 бстртипе  
 Ссылочный тип в виде форматированной строки.  
  
 бстрвалуе  
 Ссылочное значение в виде форматированной строки  
  
 дваттриб  
 Сочетание флагов из перечисления [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) , которое задает флаги для атрибутов свойств отладки.  
  
 дврефтипе  
 Значение из перечисления [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) , указывающее, является ли ссылочный тип строгим или слабым.  
  
 m_pReference  
 Объект [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , указывающий справочные сведения.  
  
## <a name="remarks"></a>Remarks  
 Эта структура передается в вызов метода [жетреференцеинфо](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) , который должен быть заполнен. Эта структура также возвращается как часть списка из интерфейса [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) , который, в свою очередь, возвращается из вызова метода [енумчилдрен](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)   
 [жетреференцеинфо](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)   
 [енумчилдрен](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)

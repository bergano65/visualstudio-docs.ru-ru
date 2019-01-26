---
title: IDebugReference2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c6e68785640e68aa6fe4641528ca2f96d3c8406
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54978286"
---
# <a name="idebugreference2"></a>IDebugReference2
Этот интерфейс представляет ссылку на свойство фрейма стека или некоторые другие свойства.  
  
> [!NOTE]
>  `IDebugReference2` зарезервирован для использования в будущем и все его методы должны возвращать `E_NOTIMPL`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс, представляющий ссылку на конкретный вид значение. Например значение может представлять числовое значение в результате вычисления выражения, контекста памяти, используемый для отображения в памяти, или список регистров и их значения.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовите [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) для получения этого интерфейса. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) и [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) также возвращать этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugReference2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Получает [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структура, описывающая эту ссылку.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Задает значение этой ссылки из строки.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Задает значение этой ссылки из другой ссылки.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Перечисляет дочерние элементы данной ссылки.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Возвращает родительский объект этой ссылки.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Получает ссылку на самого дальнего этой ссылки.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Возвращает байт памяти, на которые ссылается эта ссылка.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Получает контекст памяти для этой ссылки.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Возвращает размер в байтах, этой ссылки.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Задает этот ссылочный тип.|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Сравнивает эту ссылку с другим.|  
  
## <a name="remarks"></a>Примечания  
  
> [!NOTE]
>  Такое использование «свойства» не следует путать с, то есть переменную-член класса, несмотря на то что `IDebugReference2` может представлять такая сущность.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) представляет свойство, хотя `IDebugReference2` представляет ссылку на свойство, обычно ссылку на объект в отлаживаемой программы.  
  
 Основное различие между свойством и ссылка является то, что свойство относится к именованному экземпляру объекта, пока ссылка ссылается на экземпляр без имени. Например, свойство может ссылаться на объект в куче программы по `"a.b"`. Еще одно свойство может ссылаться на один и тот же объект как `"c.d"`. Способ обращения к этому свойству необходимо, `"a.b"` или `"c.d"` находиться в области видимости. Ссылка на этот же объект является безымянным; объект можно ссылаться до тех пор, пока память для этого объекта является допустимым.  
  
 `IDebugProperty2` Интерфейс может рассматриваться как значение с именем, типом и адрес. `IDebugReference2`, С другой стороны, может рассматриваться как тип и адрес.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
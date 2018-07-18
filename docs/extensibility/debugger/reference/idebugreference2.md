---
title: IDebugReference2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb5d5d8b3ab6e608a2454847fc9ec27e384777bc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121503"
---
# <a name="idebugreference2"></a>IDebugReference2
Этот интерфейс представляет ссылку на свойство кадра стека или некоторые другие свойства.  
  
> [!NOTE]
>  `IDebugReference2` Зарезервировано для будущего использования и все его методы должны возвращать `E_NOTIMPL`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс для представления ссылку на значение определенного типа. Например значение может быть числовое значение в результате вычисления выражения, контекст памяти, используемый для отображения в памяти, или список регистров и их значения.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) для получения этого интерфейса. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) и [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) также возвращают этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugReference2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Возвращает [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структура, описывающая этой ссылки.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Задает значение из этой ссылки из строки.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Задает значение из этой ссылки из другой ссылки.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Перечисляет дочерние элементы из этой ссылки.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Получает родительский элемент из этой ссылки.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Возвращает ссылку на более низкого уровня из этой ссылки.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Возвращает байт памяти, на которые ссылается эта ссылка.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Возвращает контекст памяти для этой ссылки.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Возвращает размер в байтах этой ссылки.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Задает этот ссылочный тип.|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Сравнивает с другим этой ссылки.|  
  
## <a name="remarks"></a>Примечания  
  
> [!NOTE]
>  Такое использование «свойства» не следует путать с, то есть переменную-член класса, несмотря на то что `IDebugReference2` может представлять такая сущность.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) представляет свойство, а `IDebugReference2` представляет ссылку на свойство, как правило, ссылку на объект в отлаживаемой программы.  
  
 Основное различие между свойством и ссылка — что свойство относится к именованному экземпляру объекта, пока ссылка указывает на неименованный экземпляр. Например, свойство может ссылаться на объект в куче программы по `"a.b"`. Другое свойство может ссылаться на один и тот же объект как `"c.d"`. Способ обращения к этому свойству необходимо, `"a.b"` или `"c.d"` входить в область действия. Ссылка на этот же объект является безымянным; объект можно ссылаться при условии, что память для этого объекта является допустимым.  
  
 `IDebugProperty2` Интерфейс может рассматриваться как значение с именем, типом и адрес. `IDebugReference2`, С другой стороны, можно рассматривать как тип и адрес.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
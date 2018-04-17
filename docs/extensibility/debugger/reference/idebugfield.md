---
title: IDebugField | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2ff92f339568a6a20e2f85a0b2deae9c8db244f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfield"></a>IDebugField
Этот интерфейс представляет поле, то есть описание символа или типа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Символ поставщик реализует этот интерфейс как базовый класс для всех полей.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс является базовым классом для всех полей. На основе возвращаемого значения [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), этот интерфейс может возвращать более специализированных интерфейсов с помощью [QueryInterface](/cpp/atl/queryinterface). Кроме того, многие интерфейсы возвращают `IDebugField` объекты из различных методов.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugField`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Возвращает отображаемую информацию о символов или типа.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Возвращает тип поля.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Возвращает тип поля.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Получает контейнер поля.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Получает адрес поля.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Получает размер поля в байтах.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Возвращает расширенные сведения о поле.|  
|[Равно](../../../extensibility/debugger/reference/idebugfield-equal.md)|Сравнивает два поля.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Получает сведения зависят от типов о символа или типа.|  
  
## <a name="remarks"></a>Примечания  
 Тип эквивалентен языка C `typedef`.  
  
 В следующем примере язык C++ `weather` является типом класса и `sunny` и `stormy` являются символами:  
  
```cpp  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Можно определить тип путем вызова ли поле представляет символ [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) и проверив [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) результат. Если `FIELD_KIND_TYPE` установлен бит, поле имеет тип и если `FIELD_KIND_SYMBOL` установлен бит, это символ.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
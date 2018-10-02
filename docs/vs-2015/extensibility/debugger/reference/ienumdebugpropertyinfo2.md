---
title: IEnumDebugPropertyInfo2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3becd764a391e3f3516886efd630b06125fc211f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573192"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IEnumDebugPropertyInfo2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugpropertyinfo2).  
  
Этот интерфейс перечисляет [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления информации для конкретного свойства.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовите [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) для получения этого интерфейса, представляющую дочерние узлы определенного свойства. Вызовите [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) для получения этого интерфейса, представляющих заданные свойства определенный кадр стека.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugPropertyInfo2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Извлекает указанное число [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структур в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Пропускает заданное число [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структур в последовательности перечисления.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Получает число [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структур в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 В общем случае свойство — это иерархия, сведения, которые могут включать имя, значение, адрес и тип, а также любые другие сведения, соответствующий кадру стека или объект связанного свойства. См. в разделе [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) для получения дополнительных сведений.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)


---
title: "IEnumDebugPropertyInfo2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPropertyInfo2
helpviewer_keywords: IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9e7f261a449e20873183ff59487c1a6b2df6b678
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Этот интерфейс перечисляет [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления сведений для определенного свойства.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) для получения этого интерфейса, представляющую дочерние узлы определенного свойства. Вызовите [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) получить этот интерфейс, представляющий свойства определенного кадра стека.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugPropertyInfo2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Извлекает указанное число [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Пропускает указанное число [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры в последовательности перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[Клон](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Создает перечислитель, с тем же состоянием, как у текущего перечислителя.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Возвращает число [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Как правило свойство представляет собой иерархию сведения, которые могут включать имя, значение, адрес и тип, а также любые другие данные, соответствующий кадру стека или объект связанного свойства. В разделе [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) для получения дополнительных сведений.  
  
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
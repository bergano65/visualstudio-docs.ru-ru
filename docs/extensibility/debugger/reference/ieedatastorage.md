---
title: "IEEDataStorage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEDataStorage
helpviewer_keywords: IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: daf5f3e7547ee32b641ccf4c1448eaa9a80b72fa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ieedatastorage"></a>IEEDataStorage
Этот интерфейс представляет собой массив байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений (Эстония) реализует этот интерфейс для представления массива байтов (используемые визуализаторами типов для извлечения и изменения данных в [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) интерфейс). Обычно EE реализует этот интерфейс для поддержки визуализаторы внешнего типа.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Методы в `IPropertyProxyEESide` все интерфейса возвращают этот интерфейс. Вызовите [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) для получения [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) интерфейса. Вызовите [QueryInterface](/cpp/atl/queryinterface) на [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс для получения [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 `IEEDataStorage` Интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Получает указанное число байтов данных для предоставленного буфера.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Возвращает число доступных байтов данных.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс для доступа к данным, удерживаемые объекта используется тип визуализатора. Эти данные обрабатываются как массив байтов, что позволяет работать с ним так, как требуется, чтобы предлагать пользователю визуализатор типа.  
  
 Пользовательское средство просмотра можно также использовать этот интерфейс, при необходимости, хотя чаще, пользовательское средство просмотра будет использовать пользовательский интерфейс, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) или [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (для данных, ориентированной на строку).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
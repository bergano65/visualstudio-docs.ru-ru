---
title: IPropertyProxyEESide | Документация Майкрософт
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
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a012c40026921419fee1f70b3db8294e3397079d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572653"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IPropertyProxyEESide](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ipropertyproxyeeside).  
  
Этот интерфейс предоставляет методы для просмотра данных для связанного объекта. Этот интерфейс является частью поддержки визуализаторами типов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Вычислитель выражений реализует этот интерфейс для поддержки визуализаторами типов.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовите [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) для получения этого интерфейса. Вызовите [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) на [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс для получения [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В этом интерфейсе реализованы следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Инициализирует поставщик источника данных, таким образом, чтобы доступны данные объекта.|  
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Извлекает сведения о сборке объекта.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Получает начальные данные для объекта.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Создает копию существующей с хранилищем данных.|  
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Создает ссылку на существующее хранилище данных.|  
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Извлекает сведения о конкретной сборки в контекст сборки, содержащей этот объект.|  
  
## <a name="remarks"></a>Примечания  
 Тип визуализатора использует этот интерфейс для доступа к значениям, связанный с объектом, который этот интерфейс является частью. Данных осуществляется через [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) интерфейс, который предоставляет представление только для чтения данных.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)


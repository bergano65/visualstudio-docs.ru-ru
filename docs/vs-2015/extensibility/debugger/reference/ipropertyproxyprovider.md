---
title: Ипропертипроксипровидер | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39cdc7769765a7680905fca5faa49222bf0a3b6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700047"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс предоставляет прокси-интерфейс для просмотра и изменения данных объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений (EE) реализует этот интерфейс для того же объекта, который реализует интерфейс [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) как часть поддержки визуализаторов типов в ee.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для `IDebugProperty3` интерфейса, чтобы получить этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке vtable  
 `IPropertyProxyProvider`Интерфейс реализует следующий метод:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Извлекает интерфейс прокси-сервера свойства для просмотра данных в объекте.|  
  
## <a name="remarks"></a>Remarks  
 Несмотря на то, что EE реализует этот интерфейс, реализация [жетпропертипрокси](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) обычно обрабатывается с помощью [жетпропертипрокси](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Дополнительные сведения о получении интерфейса Иивисуализерсервице см. в разделе [визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [жетпропертипрокси](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)

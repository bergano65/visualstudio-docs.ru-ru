---
title: IEEDataStorage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad398380c7c951b99e7d84283355ee9d31955173
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704732"
---
# <a name="ieedatastorage"></a>IEEDataStorage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет собой массив байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений (EE) реализует этот интерфейс для представления массива байтов (используемый тип визуализаторы для извлечения и изменения данных в [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) интерфейс). EE обычно реализует этот интерфейс для поддержки визуализаторы внешнего типа.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Методы в `IPropertyProxyEESide` интерфейс все возвращают этот интерфейс. Вызовите [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) для получения [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) интерфейс. Вызовите [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) на [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс для получения [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 `IEEDataStorage` Интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Извлекает указанное число байтов данных, предоставленный буфер.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Возвращает число доступных байтов данных.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс используется тип визуализатора для доступа к данным, удерживаемые определенного объекта. Эти данные обрабатываются как массив байт, обеспечивая визуализатор типов работать с ним так, как требуется, чтобы представить его пользователю.  
  
 Пользовательское средство просмотра можно также использовать этот интерфейс, при необходимости, несмотря на то, что как правило, использовать настраиваемый интерфейс, пользовательское средство просмотра [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) или [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (для данных, ориентированных на строку).  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

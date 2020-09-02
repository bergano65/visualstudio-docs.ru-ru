---
title: Иидатастораже | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704732"
---
# <a name="ieedatastorage"></a>IEEDataStorage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет массив байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений (EE) реализует этот интерфейс для представления массива байтов (используемый визуализаторами типов для извлечения и изменения данных через интерфейс [ипропертипроксеесиде](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) ). EE обычно реализует этот интерфейс для поддержки визуализаторов внешних типов.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Методы в `IPropertyProxyEESide` интерфейсе возвращают этот интерфейс. Вызовите [жетпропертипрокси](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) , чтобы получить интерфейс [ипропертипроксеесиде](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Вызовите [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) в интерфейсе [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , чтобы получить интерфейс [ипропертипроксипровидер](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке vtable  
 `IEEDataStorage`Интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Извлекает указанное число байтов данных в указанный буфер.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Возвращает число доступных байтов данных.|  
  
## <a name="remarks"></a>Remarks  
 Этот интерфейс используется визуализатором типов для доступа к данным, удерживаемым конкретным объектом. Данные обрабатываются как массив байтов, что позволяет визуализатору типов манипулировать им любым способом, необходимым для представления пользователю.  
  
 Пользовательское средство просмотра также может использовать этот интерфейс, если это необходимо, хотя обычно в пользовательском средстве просмотра используется пользовательский интерфейс [жетмеморибитес](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) или [жетстрингчарс](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (для строковых данных).  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [ипропертипроксеесиде](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

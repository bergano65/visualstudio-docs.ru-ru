---
title: IDebugPropertyField | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 53b89624e1f3b929845411df0261e644191a2db5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Этот интерфейс содержит функции, позволяющие получения и задания свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Символ поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Этот интерфейс является специализацией, которая поддерживает концепцию свойства в классе.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Используйте [QueryInterface](/cpp/atl/queryinterface) получить этот интерфейс из [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейс, если [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращает `FIELD_KIND_PROP`.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) и [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейсах, этот интерфейс реализует следующие методы:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Возвращает метод, который возвращает свойство.|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Возвращает метод, который задает для свойства.|  
  
## <a name="remarks"></a>Примечания  
 Свойство — это понятие управляемого кода и представляет метод, который рассматривается как переменную. Свойства не существуют в неуправляемом коде C++.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
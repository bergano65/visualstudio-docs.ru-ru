---
title: IDebugContainerField | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: eb08e269cd5fa2d98b91d8a7ac2107e4784ca02e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Этот интерфейс представляет символ или тип, который является контейнером для других типов или символы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Символ поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейса. Этот интерфейс также является базовым классом для всех интерфейсов, которые представляют собой контейнеры.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Множество методов для многих интерфейсов возвращает этот интерфейс. Это базовый класс для всех контейнеров, более специализированных интерфейсов можно получить из этого интерфейса с помощью [QueryInterface](/cpp/atl/queryinterface). Такие интерфейсы включают [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), и [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс, этот интерфейс реализует следующий метод:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Создает перечислитель для полей контейнера.|  
  
## <a name="remarks"></a>Примечания  
 Массивы (контейнеров для переменных), классы (контейнеров для методов и переменных) и методы (содержащих параметры и локальные переменные) иллюстрируют все контейнеры.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
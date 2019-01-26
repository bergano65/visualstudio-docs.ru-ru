---
title: IDebugProgramDestroyEventFlags2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95205705d53b7040df1f8ee8fc68aab66018a362
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934456"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Включает модуль отладки переопределить поведение по умолчанию [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса при завершении сеанса отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется отладчиков. Это полезно для узлов, которые могут создавать и уничтожать нескольких программ в течение времени существования процесса.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugProgramDestroyEventFlags2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Извлекает программа уничтожить флаги.|  
  
## <a name="remarks"></a>Примечания  
 По умолчанию [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса — чтобы вернуться в режим конструктора после отправки программы все программы события уничтожения. Этот интерфейс позволяет модуля отладки изменить это поведение.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
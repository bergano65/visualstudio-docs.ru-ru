---
title: IDebugProgramDestroyEventFlags2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3d0385af4ec795608672d8d7cbdb4b188246dea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825858"
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
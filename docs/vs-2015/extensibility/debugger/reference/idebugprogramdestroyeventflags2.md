---
title: IDebugProgramDestroyEventFlags2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 86f7e211c742e4d95f3459d058139854874e7d85
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994096"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Включает модуль отладки переопределить поведение по умолчанию [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] пользовательского интерфейса при завершении сеанса отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется отладчиков. Это полезно для узлов, которые могут создавать и уничтожать нескольких программ в течение времени существования процесса.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugProgramDestroyEventFlags2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Извлекает программа уничтожить флаги.|  
  
## <a name="remarks"></a>Примечания  
 По умолчанию [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] пользовательского интерфейса — чтобы вернуться в режим конструктора после отправки программы все программы события уничтожения. Этот интерфейс позволяет модуля отладки изменить это поведение.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

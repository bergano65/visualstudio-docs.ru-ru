---
title: IDebugProcessEx2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7948fbcf4268603436ec1c0bf999d34f65a3f503
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994026"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс позволяет сеанс отладки manager (SDM) рассылать уведомления процесса, присоединение или отсоединение от процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Пользовательский порт поставщик реализует этот интерфейс на один и тот же объект как [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) интерфейс, в следующем порядке:  
  
- Отслеживание поддержки сеансы, подключенные к процессу  
  
- Поддержка автоматического присоединения через несколько отладчиков  
  
  Если он выбирает поставщика пользовательского порта можно реализовать этот интерфейс.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
  
-   Вызовы SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) на `IDebugProcess2` интерфейс для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProcessEx2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Информирует процесса о том, что сеанс теперь является отладка процесса.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Информирует процесса о том, что сеанс больше не является отладка процесса.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Добавляет узлы программы список обработчиков отладки.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс является закрытым между SDM и процессом.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Portpriv.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

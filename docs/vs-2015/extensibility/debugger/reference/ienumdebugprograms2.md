---
title: IEnumDebugPrograms2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d9d1030616fa8d7f3a1bfc6b533c4ed8433ea89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703903"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс перечисляет программы, запущенные в текущем сеансе отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс, чтобы предоставить список программ, отлаживаемых с помощью DE.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Visual Studio вызывает [енумпрограмс](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) для получения этого интерфейса. [Енумпрограмс](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) не используется в Visual Studio.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugPrograms2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Извлекает указанное количество программ в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Пропускает указанное число программ в последовательности перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Возвращает количество программ в перечислителе.|  
  
## <a name="remarks"></a>Remarks  
 Visual Studio использует этот интерфейс для:  
  
- Заполните окно " **модули** " (вызвав [енумпрограмс](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) , а затем вызвав [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) для каждой программы).  
  
- Заполните список **присоединения к процессу** (вызвав `IDebugProcess2::EnumPrograms` , а затем вызвав [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для каждого интерфейса [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , чтобы получить интерфейс [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) ).  
  
- Создать список DEs, который может выполнять отладку каждой программы в процессе (с помощью [жетенгинеинфо](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
- Примените обновления ("Изменить" и "продолжить") к каждой программе (вызвав IDebugProcess2:: Енумпрограмс, а затем вызвав [жетенкупдате](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [енумпрограмс](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

---
title: IDebugProgramEx2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d3abc956d736f5c9273134b41c0fc9c2dc7db62
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688940"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс позволяет сеанс отладки manager (SDM) присоединиться к программе и получить узел программы, связанный с программой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Пользовательский порт поставщик реализует этот интерфейс на один и тот же объект как [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс, чтобы позволить SDM присоединиться к программе в том случае, когда в то же время позволяя поставщика порта для отслеживания всех сеансов подключен к программа. Если он выбирает поставщика пользовательского порта можно реализовать этот интерфейс.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовы SDM [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) на `IDebugProgram2` интерфейс для получения этого интерфейса позволяет отслеживать сеансы, которые были присоединены к программам.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProgramEx2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Присоединяет программу к сеансу.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Получает узел программы, связанный с программой.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс является закрытым между SDM и программой.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Portpriv.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

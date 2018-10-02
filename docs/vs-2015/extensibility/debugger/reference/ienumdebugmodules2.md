---
title: IEnumDebugModules2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 26ce00fd82c9d11dbea2aa5bf02be6454558e302
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562791"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IEnumDebugModules2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugmodules2).  
  
Этот интерфейс перечисляет список модулей.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления списка модулей, загруженных для программы.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Visual Studio вызывает [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugModules2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Извлекает указанное число модулей в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Пропускает указанное число модулей в последовательности перечисления.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Возвращает число модулей.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio использует этот интерфейс в основном для того, чтобы обновить **модули** окна.  
  
 В целях отладки в Visual Studio, программа находится в логической последовательности инструкций кода, которые может пересекать границы модуля, поэтому потребность в список модулей для одного [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс. Первый модуль в списке обычно содержит начальной отправной точкой для соответствующую программу.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)


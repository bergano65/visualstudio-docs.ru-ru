---
title: IEnumDebugReferenceInfo2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 21c39c553a153707bad707d50cf5a13ae87973fd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993622"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс перечисляет [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс как часть его поддержка ссылок на объекты в памяти. Этот интерфейс должен быть реализован только в том случае, если поддерживаются ссылки.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Visual Studio вызывает [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugReferenceInfo2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Извлекает указанное число [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структур в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Пропускает заданное число [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структур в последовательности перечисления.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Получает число [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структур в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Ссылка — по существу тип и адрес, а свойство — имя, тип и адрес. Ссылка сохраняется до тех пор, пока объект называется существует в памяти. См. в разделе [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) для получения дополнительных сведений.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)

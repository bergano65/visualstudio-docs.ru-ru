---
title: "IEnumCodePaths2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumCodePaths2
helpviewer_keywords: IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a9c27084032e0492b1110b1a085ded4f8e556433
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Этот интерфейс представляет список путей кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления списка путей кода.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumCodePaths2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Извлекает указанное число путей кода в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Пропускает указанное число путей кода в последовательности перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[Клон](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Создает перечислитель, с тем же состоянием, как у текущего перечислителя.|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Возвращает количество путей кода в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Пути к коду представляет ветви точки или вызов функции в программе. Список путей кода представляет собой путь, через который заняло выполнение кода.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
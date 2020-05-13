---
title: IEnumCodePaths2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89c8cac9a7c2baa020002fe852330639d7081982
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717715"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Этот интерфейс представляет собой список путей кода.

## <a name="syntax"></a>Синтаксис

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс, чтобы представить список путей кода.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Позвоните [EnumCodePaths,](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumCodePaths2`.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Извлекает определенное количество путей кода в последовательности перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Пропускает определенное количество путей кода в последовательности перечисления.|
|[Сбросить](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md) (Клонировать)|Создает регистратор, содержащий то же состояние перечисления, что и текущий регистратор.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Получает количество путей кода в регистраторе.|

## <a name="remarks"></a>Примечания
 Путь кода представляет точку ветви или вызов функции в программе. Список путей кода представляет путь, по которому было выполнено выполнение кода.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)

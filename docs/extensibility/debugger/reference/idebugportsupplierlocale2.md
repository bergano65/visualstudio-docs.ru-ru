---
title: IDebugPortSupplierLocale2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98444ca60937d40262c92d89b8a6c48ed1a0b7ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724301"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
Предоставляет локальную поддержку поставщику порта.

## <a name="syntax"></a>Синтаксис

```
IDebugPortSupplierLocale2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик пользовательских портов реализует этот интерфейс для установки локализации.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы **IDebugPortSupplierLocale2**.

|Метод|Описание|
|------------|-----------------|
|[Setlocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Устанавливает локаль для поставщика порта.|

## <a name="requirements"></a>Требования
 Заголовок: Portpriv.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)

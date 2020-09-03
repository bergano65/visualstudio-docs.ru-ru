---
title: IDebugPortSupplierEx2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26387618b320ed56ce754e64698fbb1c4223f2f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724321"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
Обеспечивает поддержку поставщика порта для выбора и взаимодействия с основным сервером.

## <a name="syntax"></a>Синтаксис

```
IDebugPortSupplierEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Пользовательский поставщик портов реализует этот интерфейс, чтобы он мог выбрать основной сервер для использования.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы **IDebugPortSupplierEx2**.

|Метод|Описание|
|------------|-----------------|
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Задает основной сервер для поставщика порта.|

## <a name="requirements"></a>Требования
 Заголовок: Портприв. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)

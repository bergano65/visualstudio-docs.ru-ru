---
title: Поставщики портов Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6313a7afce9ed272177a26d8da1a9d1516c8022e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738295"
---
# <a name="port-suppliers"></a>Поставщики портов
В архитектуре отладчика *поставщик порта:*

- Содержится сервером и предоставляет порты по запросу этому серверу.

- Можно добавлять и удалять порты с содержащегося сервера.

- Можно перечислить все порты, которые он поставил серверу.

- Представлен интерфейсом [IDebugPortSupplier2,](../../extensibility/debugger/reference/idebugportsupplier2.md) который зарегистрирован в Visual Studio через реестр. Этот интерфейс можно получить, позвонив [в GetPortSupplier.](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]обеспечивает поставщика порта по умолчанию и порт по умолчанию. Если пользовательский порт должен быть реализован, поставщик пользовательских портов также должен быть реализован для поставки этих пользовательских портов.

## <a name="see-also"></a>См. также
- [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Порты](../../extensibility/debugger/ports.md)
- [Концепции debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)

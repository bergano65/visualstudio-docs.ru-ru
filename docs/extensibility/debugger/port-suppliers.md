---
title: Поставщики портов | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738295"
---
# <a name="port-suppliers"></a>Поставщики портов
В архитектуре отладчика *поставщик порта*:

- Содержится в сервере и предоставляет порты по запросу к этому серверу.

- Может добавлять и удалять порты на содержащем сервере.

- Может перечислить все порты, предоставленные серверу.

- Представляется интерфейсом [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , который зарегистрирован в Visual Studio в реестре. Этот интерфейс можно получить, вызвав [жетпортсупплиер](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет поставщик порта по умолчанию и порт по умолчанию. Если необходимо реализовать пользовательский порт, для предоставления этих настраиваемых портов также необходимо реализовать пользовательский порт.

## <a name="see-also"></a>См. также раздел
- [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Порты](../../extensibility/debugger/ports.md)
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)

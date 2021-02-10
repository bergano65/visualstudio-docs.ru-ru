---
title: Поставщики портов | Документация Майкрософт
description: В этой статье описывается определение и роль поставщика порта в архитектуре отладчика в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b543770e5fcc920b05e5d19a15e312174ddad3dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934394"
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

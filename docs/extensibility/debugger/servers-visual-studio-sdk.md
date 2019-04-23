---
title: Серверы (пакет SDK для Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56ec28d0d9202bfd72d31e95c53038dd1fa475e9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111783"
---
# <a name="servers-visual-studio-sdk"></a>Серверы (пакет SDK для Visual Studio)
В архитектуре отладчик *server*:

- Представляет контейнер портов и поставщикам портов и передает порты и поставщикам портов диспетчер отладки сеансов (SDM) и отладчики.

- Можно перечислить его порты и поставщикам портов и идентификации по имени.

- Представленный [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) интерфейс, который реализуется только с Visual Studio (один экземпляр сервера для каждого экземпляра работы Visual Studio).

## <a name="see-also"></a>См. также
- [Порты](../../extensibility/debugger/ports.md)
- [Поставщики портов](../../extensibility/debugger/port-suppliers.md)
- [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
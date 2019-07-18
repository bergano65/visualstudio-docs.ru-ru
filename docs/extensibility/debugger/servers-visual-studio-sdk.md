---
title: Серверы (пакет SDK для Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebd991a5bb61211a33cc965668c48644bdcf9a27
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348592"
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
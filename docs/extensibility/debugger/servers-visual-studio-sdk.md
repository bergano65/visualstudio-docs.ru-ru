---
title: Серверы (пакет SDK для Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32fdbb5afca40c3b4fced468d2f9ef0ea5226c00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712896"
---
# <a name="servers-visual-studio-sdk"></a>Серверы (пакет SDK для Visual Studio)
В архитектуре отладчика *сервер*:

- — Это контейнер портов и поставщиков портов, который передает порты и поставщики портов диспетчеру отладки сеансов (SDM) и отладчикам.

- Может идентифицировать себя по имени и перечислять его порты и поставщиков портов.

- Представляется интерфейсом [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) , который реализован только в Visual Studio (один экземпляр сервера для каждого выполняемого экземпляра Visual Studio).

## <a name="see-also"></a>См. также раздел
- [Порты](../../extensibility/debugger/ports.md)
- [Поставщики портов](../../extensibility/debugger/port-suppliers.md)
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)

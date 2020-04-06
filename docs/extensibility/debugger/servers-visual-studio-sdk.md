---
title: Серверы (Визуальная студия SDK) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712896"
---
# <a name="servers-visual-studio-sdk"></a>Серверы (пакет SDK для Visual Studio)
В архитектуре отладчика *сервер:*

- Является контейнером портов и поставщиков портов и сообщает порты и портпоставщиков сессии отладки менеджера (SDM) и отладки двигателей.

- Может идентифицировать себя по имени, и перечислить свои порты и порт поставщиков.

- Представлен интерфейсом [IDebugCoreServer2,](../../extensibility/debugger/reference/idebugcoreserver2.md) который реализуется только Visual Studio (один экземпляр сервера для каждого экземпляра запуска Visual Studio).

## <a name="see-also"></a>См. также
- [Порты](../../extensibility/debugger/ports.md)
- [Поставщики портов](../../extensibility/debugger/port-suppliers.md)
- [Концепции debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)

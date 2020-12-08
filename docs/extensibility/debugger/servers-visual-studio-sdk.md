---
title: Серверы (пакет SDK для Visual Studio) | Документация Майкрософт
description: В этой статье описывается определение и роль сервера в архитектуре отладчика в Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9eaccebf874fa5fc0e7aaf63823547742215a568
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845301"
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

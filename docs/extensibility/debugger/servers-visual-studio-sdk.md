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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d60c214fce57f5958d8b30ca231c3e8a2bc05194
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960810"
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

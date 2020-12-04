---
title: Модули | Документация Майкрософт
description: В этой статье описывается определение и роль модуля в архитектуре отладчика в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 57202231c1bbfc7712d322b8cc7a30e3f64c87af
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606649"
---
# <a name="modules"></a>Модули
В плане архитектуры отладчика это *модуль*:

- — Это физический контейнер кода, например исполняемый файл или библиотека DLL.

- Может перезагружать свои символы и описывать саму себя. Описания модулей отображаются в окне Модули интегрированной среды разработки.

- Представляется интерфейсом [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , созданным модулем отладки для описания модуля.

## <a name="see-also"></a>См. также
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)

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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9aa0aaf7e82287c1dc2e35c524798a3480d2573e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926332"
---
# <a name="modules"></a>Модули
В плане архитектуры отладчика это *модуль*:

- — Это физический контейнер кода, например исполняемый файл или библиотека DLL.

- Может перезагружать свои символы и описывать саму себя. Описания модулей отображаются в окне Модули интегрированной среды разработки.

- Представляется интерфейсом [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , созданным модулем отладки для описания модуля.

## <a name="see-also"></a>См. также раздел
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)

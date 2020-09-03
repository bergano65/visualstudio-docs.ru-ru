---
title: Модули | Документация Майкрософт
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
ms.openlocfilehash: abdf76c7f5f031d2ef7f3bcac2bae8a2c508b783
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738349"
---
# <a name="modules"></a>Модули
В плане архитектуры отладчика это *модуль*:

- — Это физический контейнер кода, например исполняемый файл или библиотека DLL.

- Может перезагружать свои символы и описывать саму себя. Описания модулей отображаются в окне Модули интегрированной среды разработки.

- Представляется интерфейсом [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , созданным модулем отладки для описания модуля.

## <a name="see-also"></a>См. также раздел
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)

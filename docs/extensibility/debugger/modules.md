---
title: Модули | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f31e3760a0697be8c9fc80eb811c99df79d32b1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718915"
---
# <a name="modules"></a>Модули
С точки зрения архитектуры отладчика *модуль*:

-   — Это физический контейнер кода, например исполняемый файл или библиотеку DLL.

-   Можно перезагрузить его символы и описать сам себя. Описание модуля, отображаются в интегрированной среды разработки окна "Модули".

-   Представленный [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) интерфейса, созданные модуля отладки для описания модуля.

## <a name="see-also"></a>См. также
- [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
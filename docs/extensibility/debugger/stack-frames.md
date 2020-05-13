---
title: Стек кадры Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ea79ad199e20afeb5d2bf1ca6a3cf881c6d51c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712844"
---
# <a name="stack-frames"></a>Стек кадры
В архитектуре отладчика *кадр стеков:*

- Является абстракцией стека, обеспечивающей контекст выполнения потока. Поток всегда выполняется в функции. Рамка стека содержит локальные переменные функции и аргументы к ней. Для отладки с помощью Visual Studio отладка языка или среды должна поддерживать кадры стека.

- Может как идентифицировать, так и описать себя, и может вернуть связанный поток. Кадр стека может также возвращать контекст кода, представляющий текущий указатель инструкции, и связанные с ней контексты оценки документации и выражения.

- Обладает свойствами, описывающие имя, тип и значение локальных переменных и аргументов, и которые отображаются в различных окнах отладки IDE.

- Представлен интерфейсом [IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) обычно созданным движком отладки (DE) или виртуальной машиной в результате выполнения потока.

## <a name="see-also"></a>См. также
- [Контексты debugger](../../extensibility/debugger/debugger-contexts.md)
- [Концепции debugger](../../extensibility/debugger/debugger-concepts.md)
- [Двигатель debug](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)

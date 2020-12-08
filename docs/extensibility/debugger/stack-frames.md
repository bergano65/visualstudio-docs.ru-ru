---
title: Кадры стека | Документация Майкрософт
description: В этой статье описывается определение и роль кадра стека в архитектуре отладчика в Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ab2c891002ad90d767a4c5ca9efffd3f3d1d10ee
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845210"
---
# <a name="stack-frames"></a>Кадры стека
В архитектуре отладчика *кадр стека*:

- — Это абстракция стека, который предоставляет контекст выполнения потока. Поток всегда выполняется внутри функции. Кадр стека содержит локальные переменные функции и ее аргументы. Для отладки в Visual Studio язык или окружение, для которых выполняется отладка, должны поддерживать кадры стека.

- Может одновременно идентифицировать и описать себя, а также может возвращать связанный поток. Кадр стека также может возвращать контекст кода, который представляет текущий указатель инструкции, а также связанную документацию и контекст оценки выражения.

- Имеет свойства, описывающие имя, тип и значение локальных переменных и аргументов, которые отображаются в различных окнах отладки интегрированной среды разработки.

- Представляется интерфейсом [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , обычно созданным модулем отладки (de) или виртуальной машиной, как следствие выполнения потока.

## <a name="see-also"></a>См. также раздел
- [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [Модуль отладки](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)

---
title: Контроль исполнения и государственная оценка (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc76ae97e8baa6ce78dd4d565109d6a19e2051e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738750"
---
# <a name="execution-control-and-state-evaluation"></a>Контроль исполнения и государственная оценка
Для отладки приложения требуется реализация таких функций управления выполнением, как входить в функции, останавливаться в точках разрыва и продолжать выполнение. Отладка Visual Studio основывает контроль выполнения на событиях, отправляемых между компонентами отладчика.

## <a name="in-this-section"></a>В этом разделе
 [Контроль программы](../../extensibility/debugger/program-control.md) Перечисляет следующие процедуры, возникающие на уровне программы: настройка следующего оператора, выполнение, шаг, продолжение, приостановка и возобновление.

 [Методы, связанные с брейк-пойнтами](../../extensibility/debugger/breakpoint-related-methods.md) Определяет связанные и ожидающие типы точек разрыва, которые поддерживает Visual Studio.

 [Оценка стека вызова](../../extensibility/debugger/call-stack-evaluation.md) Обсуждается реализация методов, позволяющих просматривать кадры стека стека стеков во время перерыва.

 [Оценка экспрессии](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Объясняет, как движок отладки (DE), оценка выражения (EE) и диспетчер сеансов участвуют в разборе и оценке выражения, внесенного в одно из окон IDE.

 [Управление событиями](../../extensibility/debugger/control-events.md) Обсуждает интерфейс, используемый для отправки событий во время контролируемого выполнения программы.

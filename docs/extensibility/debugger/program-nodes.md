---
title: Узлы программы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2943f74c7316495be93c2f5c20998ffa685f5d01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738215"
---
# <a name="program-nodes"></a>Узлы программы
В архитектуре отладчика — *узел программы*:

- — Это упрощенное описание программы.

- Может идентифицировать себя и процесс, в котором он выполняется. Узел программы можно присоединить к, отсоединить от и описать подсистему отладки (DE), в которой он был создан, если таковой имеется.

- Представляется интерфейсом [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , который обычно создается методом de или Port. Узлы программы добавляются в порт путем вызова [аддпрограмноде](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). При добавлении к порту узла программы он добавляется в процесс, содержащий программу, которую представляет этот узел программы.

  Иногда после запуска сеанса отладки, в зависимости от реализации пакета отладки, узлы программы используются для создания соответствующих программ. Когда процесс запрашивается для своих программ, выполняется перечисление программ, по одному для каждого узла программы.

  Перед присоединением программы к среде IDE требуется только упрощенное описание программы. Эти сведения можно получить из узла программы. После того как программа подключена к, в интегрированной среде разработки отображаются более подробные сведения, например список всех потоков, выполняющихся в программе. Эти сведения получаются из самой программы.

## <a name="see-also"></a>См. также раздел
- [Программы](../../extensibility/debugger/programs.md)
- [Процессы](../../extensibility/debugger/processes.md)
- [Модуль отладки](../../extensibility/debugger/debug-engine.md)
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)

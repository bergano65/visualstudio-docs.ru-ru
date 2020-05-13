---
title: Узлы программы Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738215"
---
# <a name="program-nodes"></a>Узлы программы
В архитектуре отладчика *узло программы:*

- Является легким описанием программы.

- Может идентифицировать себя и процесс, в который он работает. Узла программы можно прикрепить, отсоединить от двигателя отладки (DE), который создал его, если таковые имеется.

- Представлен интерфейсом [IDebugProgramNode2,](../../extensibility/debugger/reference/idebugprogramnode2.md) обычно созданным DE или портом. Узлы программы добавляются в порт, позвонив [в AddProgramNode.](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) Когда узла программы добавляется в порт, он добавляется к процессу, содержащему программу, которую представляет этот узлы программы.

  Через некоторое время после начала сеанса отладки, в зависимости от реализации пакета отладок, узлы программы используются для создания соответствующих программ. Когда процесс запрашивается для своих программ, программы перечисляются, по одному для каждого узла программы.

  Перед присоединением программы IDE требуется только легкое описание программы. Эта информация может быть получена из узла программы. Как только программа прикреплена к программе, IDE отображает более подробную информацию, например список всех потоков, работающих в программе. Эта информация получена из самой программы.

## <a name="see-also"></a>См. также
- [Программы](../../extensibility/debugger/programs.md)
- [Процессов](../../extensibility/debugger/processes.md)
- [Двигатель debug](../../extensibility/debugger/debug-engine.md)
- [Концепции debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)

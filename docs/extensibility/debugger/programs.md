---
title: Программы Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3fd1db5add74d2d94467e1f369916feb5f30d4a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738205"
---
# <a name="programs"></a>Программы
В архитектуре отладчика *программа:*

- Является контейнером как для набора потоков, так и для набора модулей. Программа не имеет единой аналогии в операционной системе Windows.

     Программа является своего рода подпроцесс. Например, при отладке веб-узла скрипт можно рассматривать как программу. В то время как скрипт работает в процессе создания скриптов, независимо от других скриптов, он также имеет свой собственный набор потоков. Отладка двигателя (DE) прикрепляется к программе, а не к процессу или потоку.

- Может идентифицировать себя и процесс, в который он работает. Программа может быть прикреплена к, быть отделена от, и описать DE, который создал его, если таковые имеется. Программа также может выполняться, останавливаться, продолжать и быть прекращена.

- Можно перечислить все его потоки. Программа также может предоставить свой собственный поток разборок и перечислить все контексты кода данной позиции документа.

- Представлен интерфейсом [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) созданным до присоединения программы или как часть процесса присоединения, в зависимости от реализации. Когда порт перечисляет программы процесса, каждая программа создается в соответствии с соответствующим интерфейсом [IDebugProgramNode2,](../../extensibility/debugger/reference/idebugprogramnode2.md) передаваемым в качестве аргумента [addProgramNode.](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) В то время `IDebugProgram2` как отладка двигателей также создавать интерфейсы для представления программ, эти программы не создаются в соответствии с узлом программы. Интерфейсы, `IDebugProgramNode2` созданные DE, используются для фактической отладки, в то время как интерфейсы, созданные портом, используются только для обнаружения, какие программы работают в процессе.

## <a name="see-also"></a>См. также
- [Процессов](../../extensibility/debugger/processes.md)
- [Узлы программы](../../extensibility/debugger/program-nodes.md)
- [Модули](../../extensibility/debugger/modules.md)
- [Концепции debugger](../../extensibility/debugger/debugger-concepts.md)
- [Двигатель debug](../../extensibility/debugger/debug-engine.md)
- [Позиция документа](../../extensibility/debugger/document-position.md)
- [Контекст кода](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)

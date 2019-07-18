---
title: Службы, нехватке памяти выполнение отладчика | Документация Майкрософт
ms.date: 07/10/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.debug_no_memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger
author: isadorasophia
ms.author: isgarcia
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 05664ffd056f69215e6fb00d6d49a59382a3692f
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "67854021"
---
# <a name="debugger-services-running-out-of-memory"></a>Службы, нехватке памяти выполнение отладчика
Отладка служб не хватает памяти и вызвало завершение сеанса отладки.

## <a name="to-investigate-this-error-on-windows"></a>Чтобы изучить эту ошибку в Windows
- Можно вернуть на графе памяти процесса **средства диагностики** окно, чтобы просмотреть, если целевое приложение испытывает огромное увеличение памяти. Если Да, использовать **использование памяти** средство для диагностики, что является основную причину проблемы, см. в разделе [анализ использования памяти](../profiling/memory-usage.md).

- Если целевое приложение не потребляют большой объем памяти, используйте **диспетчер задач** окно, чтобы извлечь использование памяти Visual Studio (devenv.exe), рабочего процесса (msvsmon.exe), или VS Code (vsdbg.exe/vsdbg-ui.exe) для Определите, если это проблема отладчика. Если хватает памяти процесса devenv.exe, уменьшите количество поддерживаемые обозревателем расширения Visual Studio.

## <a name="see-also"></a>См. также
- [Запись блога. Анализ ресурсов ЦП и памяти во время отладки](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Об управлении памятью](/windows/win32/memory/about-memory-management)

---
title: В службах отладчика недостаточно памяти | Документация Майкрософт
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
ms.openlocfilehash: 12215f9c740e68c4f2749a51b06c09a1385dae1a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737844"
---
# <a name="debugger-services-running-out-of-memory"></a>Службам отладки недостаточно памяти
В службах отладки недостаточно памяти, что привело к завершению сеанса отладки.

## <a name="to-investigate-this-error-on-windows"></a>Анализ этой ошибки в Windows
- Можно проверить граф памяти процесса в окне **средства диагностики** , чтобы определить, испытывает ли целевое приложение огромное увеличение памяти. Если это так, используйте средство **использования памяти** для диагностики базовой проблемы, см. раздел [Анализ использования памяти](../profiling/memory-usage.md).

- Если целевое приложение не потребляет много памяти, используйте окно **диспетчера задач** для извлечения сведений об использовании памяти в Visual Studio (devenv. exe), рабочем процессе (msvsmon. exe) или VS Code (vsdbg. exe/всдбг-УИ. exe), чтобы определить, является ли это проблема с отладчиком. Если для процесса, в котором не хватает памяти, используется файл devenv. exe, рассмотрите возможность сокращения числа выполняющихся расширений Visual Studio.

## <a name="see-also"></a>См. также
- [Запись блога: анализ ЦП и памяти во время отладки](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Сведения об управлении памятью](/windows/win32/memory/about-memory-management)

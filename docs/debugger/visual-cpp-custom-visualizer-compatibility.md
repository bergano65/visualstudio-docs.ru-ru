---
title: Пользовательский визуализатор совместимости Visual C/C++
ms.date: 01/28/2019
ms.prod: visual-studio-dev16
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 32e38dd3bba8a1127d8756972b73e8b47a514f1b
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335185"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Пользовательский визуализатор совместимости Visual C/C++

Начиная с Visual Studio 2019 по Visual C++ включает Улучшенный отладчик, который использует 64-разрядный внешний процесс для размещения его компонентов с интенсивным использованием памяти. В рамках этого обновления необходимо обновить расширения, определенные средству оценки выражений Visual C/C++ для обеспечения их совместимости с помощью нового отладчика.

В настоящее время при использовании устаревших addin EE C/C++ или C/C++ пользовательский визуализатор, об использовании этого внешнего процесса, выбрав можно отключить **средства** > **параметры**  >   **Отладка**и сняв **нагрузки отладочные символы во внешнем процессе (только машинный код)**. Если вы отмените выбор этого параметра, возникнет значительное увеличение использования памяти в процессе интегрированной среды разработки (devenv.exe). Таким образом Если ожидается, что отладка больших проектов, рекомендуется работать с владельцем расширения, чтобы обеспечить совместимость с этот параметр отладки.

Если вы являетесь владельцем устаревших addin EE C/C++ или C/C++ пользовательский визуализатор, можно найти дополнительные сведения о позволило загружающие расширение в рабочем процессе на [Concord расширяемости примеры вики-сайте](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Также можно найти [пример пользовательского визуализатора на C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).
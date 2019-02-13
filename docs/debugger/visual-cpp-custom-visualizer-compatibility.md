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
ms.assetid: 64af5bed-e38b-420f-b9ce-d64f35100aae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: a51f2d87b432bf6f4a3925b55622273b56cf5c32
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920968"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Пользовательский визуализатор совместимости Visual C/C++

Начиная с Visual Studio 2019 по Visual C++ включает Улучшенный отладчик, который использует 64-разрядный внешний процесс для размещения его компонентов с интенсивным использованием памяти. В рамках этого обновления необходимо обновить расширения, определенные средству оценки выражений Visual C/C++ для обеспечения их совместимости с помощью нового отладчика.

В настоящее время при использовании устаревших addin EE C/C++ или C/C++ пользовательский визуализатор, об использовании этого внешнего процесса, выбрав можно отключить **средства** > **параметры**  >   **Отладка**и сняв **нагрузки отладочные символы во внешнем процессе (только машинный код)**. Если вы отмените выбор этого параметра, возникнет значительное увеличение использования памяти в процессе интегрированной среды разработки (devenv.exe). Таким образом Если ожидается, что отладка больших проектов, рекомендуется работать с владельцем расширения, чтобы обеспечить совместимость с этот параметр отладки.

Если вы являетесь владельцем устаревших addin EE C/C++ или C/C++ пользовательский визуализатор, можно найти дополнительные сведения о позволило загружающие расширение в рабочем процессе на [Concord расширяемости примеры вики-сайте](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Также можно найти [пример пользовательского визуализатора на C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).
---
title: Visual C /C++ пользовательский визуализатор совместимости
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901170"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C /C++ пользовательский визуализатор совместимости

Начиная с Visual Studio 2019 г., Visual C++ включает в себя Улучшенный отладчик, который использует 64-разрядный внешний процесс для размещения его компонентов с интенсивным использованием памяти. В рамках этого обновления определенных расширений для Visual C /C++ вычислитель выражений необходимо обновить, чтобы обеспечить их совместимость с помощью нового отладчика.

В настоящее время при использовании прежних версий C /C++ EE addin или C /C++ пользовательский визуализатор можно отключить использование этого внешнего процесса, выбрав **средства** > **параметры**  >  **Отладка**и сняв **нагрузки отладочные символы во внешнем процессе (только машинный код)**. Если вы отмените выбор этого параметра, возникнет значительное увеличение использования памяти в процессе интегрированной среды разработки (devenv.exe). Таким образом Если ожидается, что отладка больших проектов, рекомендуется работать с владельцем расширения, чтобы обеспечить совместимость с этот параметр отладки.

Если вы являетесь владельцем прежних версий C /C++ EE addin или C /C++ пользовательский визуализатор можно найти дополнительные сведения о позволило загружающие расширение в рабочем процессе на [Concord расширяемости примеры вики-сайте](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Также можно найти [C /C++ пример пользовательский визуализатор](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).
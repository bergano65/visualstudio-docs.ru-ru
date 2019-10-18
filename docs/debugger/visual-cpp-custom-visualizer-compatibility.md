---
title: Совместимость с VisualC++ C/Пользовательский визуализатор
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
ms.openlocfilehash: 9fdd44be89fde2fbc26038c8b88fff405876264f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430615"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Совместимость с VisualC++ C/Пользовательский визуализатор

Начиная с Visual Studio 2019, C++ включает улучшенный отладчик, использующий внешний процесс с 64-битным процессом для размещения компонентов с большим объемом памяти. В рамках этого обновления необходимо обновить некоторые расширения для средства оценки выраженийC++ C/, чтобы сделать их совместимыми с новым отладчиком.

Если в настоящее время используется устаревшая надстройка CC++ /ee или c/C++ Пользовательский визуализатор, можно отключить использование этого внешнего процесса, перейдя в **меню Сервис**  > **Параметры**  > **Отладка**, а затем отменив **загрузку загрузки. символы во внешнем процессе (только машинный код)** . Если отменить выбор этого параметра, произойдет значительное увеличение использования памяти в рамках процесса IDE (devenv. exe). Таким образом, если предполагается Отладка больших проектов, рекомендуется работать с владельцем расширения, чтобы сделать его совместимым с этим параметром отладки.

Если вы являетесь владельцем устаревшей надстройки C/C++ ee или c/C++ Custom визуализатора, дополнительные сведения о том, как загрузит расширение в рабочий процесс, см. на вики- [сайте примеры расширения Конкорд](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Вы также можете найти [пример для CC++ /настраиваемого визуализатора](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).
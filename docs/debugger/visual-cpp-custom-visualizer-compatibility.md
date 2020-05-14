---
title: Совместимость пользовательского визуализатора Visual C/C++
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
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430615"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Совместимость пользовательского визуализатора Visual C/C++

Начиная с версии Visual Studio 2019, C++ включает улучшенный отладчик, использующий внешний 64-разрядный процесс для размещения компонентов, использующих большой объем памяти. В связи с этим требуется обновить некоторые расширения для оценщика выражений C/C++, чтобы обеспечить их совместимыми с новым отладчиком.

Если в настоящее время используется устаревшая надстройка C/C++ EE или пользовательский визуализатор C/C++, можно отключить использование этого внешнего процесса. Для этого выберите **Сервис** > **Параметры** > **Отладка**, а затем снимите флажок **Загрузить символы отладки во внешнем процессе (только машинный код)** . Если отменить выбор этого параметра, использование памяти в рамках процесса IDE (devenv.exe) существенно возрастет. Таким образом, если предполагается отладка больших проектов, рекомендуется обратиться к владельцу расширения с просьбой обеспечить совместимость с этим параметром отладки.

Если вы сами являетесь владельцем устаревшей надстройки C/C++ EE или пользовательского визуализатора C/C++, ознакомьтесь с дополнительными сведения о том, как обеспечить загрузку вашего расширения в рабочий процесс на [вики-сайте примеров обеспечения расширяемости Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Вы также можете найти [пример пользовательского визуализатора C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).
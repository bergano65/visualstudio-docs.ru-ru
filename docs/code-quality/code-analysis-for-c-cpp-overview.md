---
title: Общие сведения об анализе кода в C/C++
ms.date: 04/28/2018
ms.topic: conceptual
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 07ba2c64be0af987b82c870b89d3451b5d48d28f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55947644"
---
# <a name="code-analysis-for-cc-overview"></a>Анализ кода для C/C++ Обзор

Средство анализа кода C/C++ предоставляет сведения о возможных дефектах в исходном коде C/C++. К наиболее распространенным ошибкам кодирования, которые обнаруживает данное средство, относятся переполнение буфера, неинициализированная память, разыменования пустых указателей, а также утечки памяти и ресурсов. Средство также можно запускать проверки [C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Интеграция с IDE (интегрированная среда разработки)

Средство анализа кода полностью интегрировано в Visual Studio IDE.

Во время сборки все предупреждения, созданные для исходного кода, отображаются в списке ошибок. Вы можете перейти к исходному коду, который вызвал предупреждение, и просмотреть дополнительные сведения о причине и возможные решения проблемы.

## <a name="command-line-support"></a>Поддержка командной строки

Можно также использовать средство анализа из командной строки, как показано в следующем примере:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 версии 15.7 и более поздние версии** любую систему сборки, включая CMake, можно запустить средство из командной строки.

## <a name="pragma-support"></a>Поддержка #pragma

Можно использовать `#pragma` директиву, чтобы обрабатывать предупреждения как ошибки; включить или отключить предупреждения и отключение предупреждений для отдельных строк кода. Дополнительные сведения см. в разделе [Как Задание свойств анализа кода для проектов C/C++](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Поддержка заметок

Заметки повышают точность анализа кода. Заметки содержат дополнительные сведения о предварительных и последующих условиях для параметров функции и типов возвращаемых значений. Дополнительные сведения см. в разделе [Как добавить дополнительные сведения о коде с помощью _analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Запуск средства анализа в рамках политики возврата

Вы можете предъявлять определенные требования к возвратам исходного кода. В частности, нужно убедиться, что анализ выполнялся в рамках самой последней локальной сборки. Дополнительные сведения о включении политики возврата с анализом кода см. в разделе [Создание и использование политик возврата с анализом кода](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Интеграция командного построения

Вы можете использовать интегрированные возможности системы сборки для запуска средства анализа в рамках процесса сборки [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Дополнительные сведения см. в описании [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>См. также

- [Краткое руководство. Анализ кода для C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Пошаговое руководство: Анализ кода C/C++ на наличие дефектов](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Анализ кода для предупреждений C/C++](code-analysis-for-c-cpp-warnings.md)
- [Использование средств проверки на соответствие C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
- [Ссылка проверки C++ Core Guidelines](code-analysis-for-cpp-corecheck.md)
- [Использование наборов правил для задания выполняемых правил C++](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Анализ качества драйверов с помощью средств анализа кода](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Анализ кода для драйверов предупреждений](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)

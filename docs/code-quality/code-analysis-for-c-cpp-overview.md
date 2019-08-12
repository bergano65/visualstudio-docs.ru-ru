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
ms.openlocfilehash: f7b0e29f6a9a502054b59fc7313c3eff0565f938
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919887"
---
# <a name="code-analysis-for-cc-overview"></a>Общие сведения об анализе кода в C/C++

Средство анализа кодаC++ c/Code предоставляет сведения о возможных дефектах в коде CC++ /Source. К наиболее распространенным ошибкам кодирования, которые обнаруживает данное средство, относятся переполнение буфера, неинициализированная память, разыменования пустых указателей, а также утечки памяти и ресурсов. Средство также может выполнять проверки по [ C++ основным рекомендациям](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Интеграция интегрированной среды разработки (IDE)

Средство анализа кода полностью интегрировано в интегрированную среду разработки Visual Studio.

Во время сборки все предупреждения, созданные для исходного кода, отображаются в списке ошибок. Вы можете перейти к исходному коду, который вызвал предупреждение, и просмотреть дополнительные сведения о причине и возможные решения проблемы.

## <a name="command-line-support"></a>Поддержка командной строки

Средство анализа можно также использовать из командной строки, как показано в следующем примере:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 версии 15,7 и более поздних** версий Это средство можно запустить из командной строки с любой системой сборки, включая CMak.

## <a name="pragma-support"></a>Поддержка #pragma

`#pragma` Директиву можно использовать, чтобы обрабатывать предупреждения как ошибки, включать или отключать предупреждения и подавлять предупреждения для отдельных строк кода. Дополнительные сведения см. в разделе [Директивы Pragma и ключевое слово __Pragma](https://docs.microsoft.com/cpp/preprocessor/pragma-directives-and-the-pragma-keyword).

## <a name="annotation-support"></a>Поддержка заметок

Заметки повышают точность анализа кода. Заметки содержат дополнительные сведения о предварительных и последующих условиях для параметров функции и типов возвращаемых значений. Дополнительные сведения см. [в разделе Использование аннотаций SAL для сокращенияC++ числа дефектов C/Code](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md).

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Запуск средства анализа в рамках политики возврата

Вы можете предъявлять определенные требования к возвратам исходного кода. В частности, нужно убедиться, что анализ выполнялся в рамках самой последней локальной сборки. Дополнительные сведения о включении политики возврата с анализом кода см. [в разделе Создание и использование политик возврата](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)с анализом кода.

## <a name="team-build-integration"></a>Интеграция Team Build

Вы можете использовать интегрированные возможности системы сборки для запуска средства анализа в рамках процесса сборки [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Дополнительные сведения см. в описании [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>См. также

- [Краткое руководство. Анализ кода для C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Пошаговое руководство: Анализ кода CC++ /код для дефектов](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Анализ кода для предупреждений C/C++](code-analysis-for-c-cpp-warnings.md)
- [Использование средств проверки на соответствие C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
- [C++Справочник по проверке основных правил](code-analysis-for-cpp-corecheck.md)
- [Использование наборов правил для задания выполняемых правил C++](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Анализ качества драйвера с помощью средств анализа кода](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Анализ кода для драйверов предупреждения](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)

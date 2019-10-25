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
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 515b9b7eb1b1a4d2dbee6329be782386b8370338
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806306"
---
# <a name="code-analysis-for-cc-overview"></a>Общие сведения об анализе кода в C/C++

Средство анализа кодаC++ c/Code предоставляет сведения о возможных дефектах в коде CC++ /Source. К наиболее распространенным ошибкам кодирования, которые обнаруживает данное средство, относятся переполнение буфера, неинициализированная память, разыменования пустых указателей, а также утечки памяти и ресурсов. Средство также может выполнять проверки по [ C++ основным рекомендациям](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Интеграция интегрированной среды разработки (IDE)

Средство анализа кода полностью интегрировано в интегрированную среду разработки Visual Studio.

Во время сборки все предупреждения, созданные для исходного кода, отображаются в списке ошибок. Вы можете перейти к исходному коду, который вызвал предупреждение, и просмотреть дополнительные сведения о причине и возможные решения проблемы.

## <a name="command-line-support"></a>Поддержка командной строки

Средство анализа можно также использовать из командной строки, как показано в следующем примере:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 версии 15,7 и более поздних версий:** Это средство можно запустить из командной строки с любой системой сборки, включая CMak.

## <a name="pragma-support"></a>Поддержка #pragma

Можно использовать директиву `#pragma`, чтобы обрабатывать предупреждения как ошибки; Включение и отключение предупреждений, а также отключение предупреждений для отдельных строк кода. Дополнительные сведения см. в разделе [Директивы Pragma и ключевое слово __Pragma](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword).

## <a name="annotation-support"></a>Поддержка заметок

Заметки повышают точность анализа кода. Заметки содержат дополнительные сведения о предварительных и последующих условиях для параметров функции и типов возвращаемых значений. Дополнительные сведения см. [в разделе Использование аннотаций SAL для сокращенияC++ числа дефектов C/Code](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md).

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Запуск средства анализа в рамках политики возврата

Вы можете предъявлять определенные требования к возвратам исходного кода. В частности, нужно убедиться, что анализ выполнялся в рамках самой последней локальной сборки. Дополнительные сведения о включении политики возврата с анализом кода см. [в разделе Создание и использование политик возврата с анализом](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)кода.

## <a name="team-build-integration"></a>Интеграция Team Build

Вы можете использовать интегрированные возможности системы сборки для запуска средства анализа в рамках процесса сборки [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Дополнительные сведения см. в описании [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>См. также

- [Краткое руководство. анализ кода для C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Пошаговое руководство.C++ анализ C/кода на наличие дефектов](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Анализ кода для предупреждений C/C++](code-analysis-for-c-cpp-warnings.md)
- [Использование средств проверки на соответствие C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
- [C++Справочник по проверке основных правил](code-analysis-for-cpp-corecheck.md)
- [Использование наборов правил для задания выполняемых правил C++](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Анализ качества драйвера с помощью средств анализа кода](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Анализ кода для драйверов предупреждения](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)

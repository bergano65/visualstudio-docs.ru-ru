---
title: Общие сведения об анализе кода в C/C++
ms.date: 04/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: ea576ba794350e6cee6b20f8ef9adb62f82a9c51
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2018
---
# <a name="code-analysis-for-cc-overview"></a>Анализ кода для C/C++ Обзор

Средство анализа кода C/C++ предоставляет сведения о возможных дефектах в исходном коде C/C++. К наиболее распространенным ошибкам кодирования, которые обнаруживает данное средство, относятся переполнение буфера, неинициализированная память, разыменования пустых указателей, а также утечки памяти и ресурсов. Программа также может запустить проверки [C++ основные рекомендации](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Интеграция IDE (интегрированной среде разработки)

Средство анализа кода полностью интегрировано в Интегрированной среде разработки Visual Studio.

Во время построения все предупреждения, созданные в исходном коде отображаются в списке ошибок. Можно перейти к исходному коду, которая вызвала предупреждение, можно просмотреть дополнительные сведения о причинах и возможные решения проблемы.

## <a name="command-line-support"></a>Поддержка командной строки

Можно также использовать средство анализа из командной строки, как показано в следующем примере:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 г 15,7 и более поздних версий** систему сборки, включая CMake можно запустить средство из командной строки.

## <a name="pragma-support"></a>Поддержка #pragma

Можно использовать `#pragma` директиву, чтобы обрабатывать предупреждения как ошибки; включить или отключить предупреждения и предупреждений для отдельных строк кода. Дополнительные сведения см. в разделе [как: значение свойства анализа кода для проектов C/C++](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Поддержка заметок

Заметки улучшить точность анализа кода. Заметки предоставляют дополнительные сведения об условиях до и после в параметрах функции и типы возвращаемых значений. Дополнительные сведения см. в разделе [как: определение дополнительных сведений кода с помощью __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Запуск средства анализа в рамках политики возврата

Может потребоваться требует, что все источника возвраты кода удовлетворяют определенные политики. В частности вы хотите убедитесь в том, что анализ был проведен в рамках последнего локального построения. Дополнительные сведения о включении политику возврата с анализом кода см. в разделе [Создание и использование анализа кода возврата политик](../code-quality/creating-and-using-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Интеграция командного построения

Можно использовать интегрированных функций системы построения для запуска средства анализа кода в рамках [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] процесса построения. См. дополнительные сведения о [сборке и выпуске](/vsts/build-release/index).

## <a name="see-also"></a>См. также

- [Краткое руководство: Анализ кода для C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Пошаговое руководство: Анализ дефектов кода C/C++](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Анализ кода для предупреждений C/C++](code-analysis-for-c-cpp-warnings.md)
- [Использование средств проверки на соответствие C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
- [Справочные материалы по Проверка правила C++ основной](code-analysis-for-cpp-corecheck.md)
- [Использование наборов правил для задания выполняемых правил C++](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Анализ качества драйверов с помощью средств анализа кода](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Анализ кода для драйверов предупреждений](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)

---
title: "Анализ кода для C/C++ Обзор | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2261921e4266f1b58ed31650ac1ff1bb7c028942
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2018
---
# <a name="code-analysis-for-cc-overview"></a>Анализ кода для C/C++ Обзор

Средство анализа кода C/C++ предоставляет сведения о возможных дефектах в исходном коде C/C++. Наиболее распространенные ошибки, обнаруживаемые этим средством: переполнение буфера, неинициализированная память, разыменование пустых указателей, а также утечка памяти и ресурсов.  
  
## <a name="ide-integrated-development-environment-integration"></a>Интеграция в интегрированную среду разработки  
 Для более удобного использования разработчиками средство анализа, она полностью интегрировано в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки. Во время построения все предупреждения, созданные в исходном коде отображаются в списке ошибок. Можно перейти к исходному коду, которая вызвала предупреждение, можно просмотреть дополнительные сведения о причинах и возможные решения проблемы.  
  
## <a name="pragma-support"></a>#pragma поддержки  
 Разработчики могут использовать `#pragma` директиву, чтобы обрабатывать предупреждения как ошибки; включить или отключить предупреждения и предупреждений для отдельных строк кода. Дополнительные сведения см. в разделе [как: значение свойства анализа кода для проектов C/C++ ](how-to-set-code-analysis-properties-for-c-cpp-projects.md).  
  
## <a name="annotation-support"></a>Поддержка заметок  
 Заметки улучшить точность анализа кода. Заметки предоставляют дополнительные сведения об условиях до и после в параметрах функции и типы возвращаемых значений. Дополнительные сведения см. в разделе [как: определение дополнительных сведений кода с помощью __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Запуск средства анализа в рамках политики возврата  
 Может потребоваться требует, что все источника возвраты кода удовлетворяют определенные политики. В частности вы хотите убедитесь в том, что анализ был проведен в рамках последнего локального построения. Дополнительные сведения о включении политику возврата с анализом кода см. в разделе [Создание и использование анализа кода возврата политик](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Интеграция командного построения  
 Можно использовать интегрированных функций системы построения для запуска средства анализа кода в рамках [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] процесса построения. См. дополнительные сведения о [сборке и выпуске](/vsts/build-release/index).  
  
## <a name="command-line-support"></a>Поддержка командной строки  
 В дополнение к полной интеграции в среде разработки разработчики могут использовать средство анализа из командной строки, как показано в следующем примере:  
  
 `C:\>cl /analyze Sample.cpp`

## <a name="see-also"></a>См. также

[Анализ качества драйверов с помощью средств анализа кода](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)  
[Анализ кода для драйверов предупреждений](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
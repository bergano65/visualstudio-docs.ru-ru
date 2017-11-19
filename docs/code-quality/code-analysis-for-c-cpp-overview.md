---
title: "Анализ кода для C/C++ Обзор | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 55b1f4061d408187525c255e4ab12c3fe93eb60e
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2017
---
# <a name="code-analysis-for-cc-overview"></a>Общие сведения об анализе кода в C/C++
Средство анализа кода C/C++ предоставляет сведения о возможных дефектах в исходном коде C/C++. Наиболее распространенные ошибки, обнаруживаемые этим средством: переполнение буфера, неинициализированная память, разыменование пустых указателей, а также утечка памяти и ресурсов.  
  
## <a name="ide-integrated-development-environment-integration"></a>Интеграция в интегрированную среду разработки  
 Для более удобного использования разработчиками средство анализа, она полностью интегрировано в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки. Во время построения все предупреждения, созданные в исходном коде отображаются в списке ошибок. Можно перейти к исходному коду, которая вызвала предупреждение, можно просмотреть дополнительные сведения о причинах и возможные решения проблемы.  
  
## <a name="pragma-support"></a>#pragma поддержки  
 Разработчики могут использовать `#pragma` директиву, чтобы обрабатывать предупреждения как ошибки; включить или отключить предупреждения и предупреждений для отдельных строк кода. Дополнительные сведения см. в разделе [как: Включение и отключение анализа кода для определенных предупреждений C/C++](http://msdn.microsoft.com/en-us/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Поддержка заметок  
 Заметки улучшить точность анализа кода. Заметки предоставляют дополнительные сведения об условиях до и после в параметрах функции и типы возвращаемых значений. Дополнительные сведения см. в разделе [как: определение дополнительных сведений кода с помощью __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Запуск средства анализа в рамках политики возврата  
 Может потребоваться требует, что все источника возвраты кода удовлетворяют определенные политики. В частности вы хотите убедитесь в том, что анализ был проведен в рамках последнего локального построения. Дополнительные сведения о включении политику возврата с анализом кода см. в разделе [Создание и использование анализа кода возврата политик](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Интеграция командного построения  
 Можно использовать интегрированных функций системы построения для запуска средства анализа кода в рамках [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] процесса построения. Дополнительные сведения см. в разделе [Сборка приложения](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="command-line-support"></a>Поддержка командной строки  
 В дополнение к полной интеграции в среде разработки разработчики могут использовать средство анализа из командной строки, как показано в следующем примере:  
  
 `C:\>cl /analyze Sample.cpp`
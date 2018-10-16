---
title: Анализ кода для C / C++ Обзор | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
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
caps.latest.revision: 27
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 42de573efcc44437eddf0e7d098681d05c094131
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222044"
---
# <a name="code-analysis-for-cc-overview"></a>Общие сведения об анализе кода в C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Средство анализа кода C/C++ предоставляет сведения о возможных дефектах в исходном коде C/C++. Наиболее распространенные ошибки, обнаруживаемые этим средством: переполнение буфера, неинициализированная память, разыменование пустых указателей, а также утечка памяти и ресурсов.  
  
## <a name="ide-integrated-development-environment-integration"></a>Интеграция в интегрированную среду разработки  
 Для более удобного использования разработчиками средство анализа, она полностью интегрирована в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] интегрированной среды разработки. Во время сборки все предупреждения, созданные для исходного кода отображаются в списке ошибок. Можно перейти к исходному коду, которая вызвала предупреждение, можно просмотреть дополнительные сведения о причине и возможные решения проблемы.  
  
## <a name="pragma-support"></a>#pragma поддержки  
 Разработчики могут использовать `#pragma` директиву, чтобы обрабатывать предупреждения как ошибки; включить или отключить предупреждения и отключение предупреждений для отдельных строк кода. Дополнительные сведения см. в разделе [как: Включение и отключение анализа кода для определенного предупреждения C/C++](http://msdn.microsoft.com/en-us/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Поддержка заметок  
 Заметки улучшить точность анализа кода. Заметки содержатся дополнительные сведения об условиях до и после о параметров функции и типы возвращаемых значений. Дополнительные сведения см. в разделе [как: определение дополнительных сведений кода, с помощью __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Запуск средства анализа в рамках политики возврата  
 Может потребоваться требуют, что все исходного кода возвраты удовлетворять определенные политики. В частности вы хотели бы убедиться, выполнение анализа в рамках самой последней локальной сборки. Дополнительные сведения о включении политику возврата с анализом кода, см. в разделе [Создание и использование анализа кода возврата политик](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Интеграция командного построения  
 Можно использовать интегрированные функции системы построения для выполнения анализа кода в рамках [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] процесс сборки. Дополнительные сведения см. в разделе [Сборка приложения](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="command-line-support"></a>Поддержка командной строки  
 В дополнение к полной интеграции в среде разработки разработчики также могут использовать средство анализа из командной строки, как показано в следующем примере:  
  
 `C:\>cl /analyze Sample.cpp`




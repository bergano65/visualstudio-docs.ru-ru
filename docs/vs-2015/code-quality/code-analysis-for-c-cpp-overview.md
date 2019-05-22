---
title: Общие сведения об анализе кода в C/C++ | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
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
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: fce0fb33f6c536386754b10b11e724a603f0a2a6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698005"
---
# <a name="code-analysis-for-cc-overview"></a>Общие сведения об анализе кода в C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Средство анализа кода C/C++ предоставляет сведения о возможных дефектах в исходном коде C/C++. Наиболее распространенные ошибки, обнаруживаемые этим средством: переполнение буфера, неинициализированная память, разыменование пустых указателей, а также утечка памяти и ресурсов.  
  
## <a name="ide-integrated-development-environment-integration"></a>Интеграция в интегрированную среду разработки  
 Для более удобного использования разработчиками средства анализа оно полностью интегрировано в интегрированную среду разработки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Во время сборки все предупреждения, созданные для исходного кода, отображаются в списке ошибок. Вы можете перейти к исходному коду, который вызвал предупреждение, и просмотреть дополнительные сведения о причине и возможные решения проблемы.  
  
## <a name="pragma-support"></a>Поддержка #pragma  
 Разработчики могут использовать директиву `#pragma`, чтобы обрабатывать предупреждения как ошибки, включить или отключить предупреждения и отключить предупреждения для отдельных строк кода. Дополнительные сведения см. в разделе [Практическое руководство. включить и отключить анализ кода для предупреждений C/C++](https://msdn.microsoft.com/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Поддержка заметок  
 Заметки повышают точность анализа кода. Заметки содержат дополнительные сведения о предварительных и последующих условиях для параметров функции и типов возвращаемых значений. Дополнительные сведения см. в разделе [Практическое руководство. добавить дополнительные сведения о коде с помощью _analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Запуск средства анализа в рамках политики возврата  
 Вы можете предъявлять определенные требования к возвратам исходного кода. В частности, нужно убедиться, что анализ выполнялся в рамках самой последней локальной сборки. Дополнительные сведения о включении политики возврата с анализом кода см. в разделе [Создание и использование политик возврата с анализом кода](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Интеграция командного построения  
 Вы можете использовать интегрированные возможности системы сборки для запуска средства анализа в рамках процесса сборки [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]. Дополнительные сведения см. в разделе [Сборка приложения](https://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="command-line-support"></a>Поддержка командной строки  
 В дополнение к полной интеграции в среде разработки разработчики также могут использовать средство анализа из командной строки, как показано в следующем примере:  
  
 `C:\>cl /analyze Sample.cpp`

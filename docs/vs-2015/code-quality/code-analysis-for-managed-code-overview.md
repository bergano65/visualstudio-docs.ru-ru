---
title: Анализ кода для управляемого кода Обзор | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 048ea406fd9237640976f3a44bb5e53504276e0c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279374"
---
# <a name="code-analysis-for-managed-code-overview"></a>Общие сведения об анализе управляемого кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Анализа управляемого кода позволяет проанализировать управляемые сборки и получить такие сведения о сборках, как нарушения правил программирования и разработки, изложенных в руководствах по разработке Microsoft .NET Framework.  
  
 Средство анализа представляет проводимые во время анализа проверки в виде предупреждающих сообщений. В предупреждающих сообщениях указываются все проблемы, связанные с программированием и разработкой, и, по возможности, сведения о методах их устранения.  
  
## <a name="ide-integrated-development-environment-integration"></a>Интеграция в интегрированную среду разработки  
 Разработчики могут выполнять анализ кода проекта автоматически или вручную.  
  
 Чтобы запустить анализ кода при каждом построении проекта, выберите **включить анализ кода в построении (определяет константу CODE_ANALYSIS)** на странице свойств проекта. Дополнительные сведения см. в разделе [как: Включение и отключение автоматического анализа кода](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
 Чтобы запустить анализ кода вручную для проекта, на **анализ** меню, щелкните **выполнить анализ кода в**_имя_проекта_. Дополнительные сведения см. в разделе [как: Включение и отключение автоматического анализа кода](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
## <a name="rule-sets"></a>Наборы правил  
 Правила анализа управляемого кода группируются в *наборов правил*. Пользователь может воспользоваться стандартными наборами правил Майкрософт или создать настраиваемый набор правил в соответствии со своими нуждами. Дополнительные сведения см. в разделе [использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## <a name="in-source-suppression"></a>Подавление предупреждений в исходном коде  
 Зачастую удобно указать, что предупреждение неприменимо. Это позволяет сообщить разработчику и другими лицам, которые, возможно, будут проверять код позже, что предупреждение рассмотрено и либо отложено, либо проигнорировано.  
  
 Подавление предупреждений в исходном коде производится при помощи пользовательских атрибутов. Чтобы подавить предупреждение, добавьте атрибут `SuppressMessage` в исходный код, как показано в следующем примере:  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 Дополнительные сведения см. в разделе [подавления предупреждений при помощи атрибута SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Запуск анализа кода в рамках политики возврата  
 Каждая организация может предъявлять определенные требования к возвратам. В частности, может требоваться соблюдение следующих правил:  
  
-   Возвращаемый код не содержит ошибок построения.  
  
-   Анализ кода был проведен в рамках последнего построения.  
  
 Этого можно достичь, задав политики возврата. Дополнительные сведения см. в разделе [улучшение качества кода с помощью политик возврата командного проекта](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## <a name="team-build-integration"></a>Интеграция командного построения  
 Существует возможность использования интегрированных возможностей системы построения для запуска средства анализа в рамках процесса построения. Дополнительные сведения см. в разделе [Сборка приложения](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="see-also"></a>См. также  
 [Использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Практическое руководство. Включение и отключение автоматического анализа кода](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)




---
title: "Анализ кода для управляемого кода Обзор | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: b705abb680276faf9d4311cd21cae1b103c4a09d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="code-analysis-for-managed-code-overview"></a>Анализ кода для управляемого кода Обзор

Анализа управляемого кода позволяет проанализировать управляемые сборки и получить такие сведения о сборках, как нарушения правил программирования и разработки, изложенных в руководствах по разработке Microsoft .NET Framework.

Средство анализа представляет проводимые во время анализа проверки в виде предупреждающих сообщений. В предупреждающих сообщениях указываются все проблемы, связанные с программированием и разработкой, и, по возможности, сведения о методах их устранения.

## <a name="ide-integrated-development-environment-integration"></a>Интеграция IDE (интегрированной среде разработки)

Можно выполнять анализ кода проекта автоматически или вручную.

Чтобы запустить анализ кода при каждом построении проекта, выберите **включить анализ кода в построении** на странице свойств проекта. Дополнительные сведения см. в разделе [как: Включение и отключение автоматического анализа кода](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Чтобы вручную запустить анализ кода для проекта, в строке меню выберите **анализ** > **выполнить анализ кода** > **выполнить анализ кода в <project>** . Дополнительные сведения см. в разделе [как: Включение и отключение автоматического анализа кода](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="rule-sets"></a>Наборы правил

Правила анализа управляемого кода группируются в *наборов правил*. Пользователь может воспользоваться стандартными наборами правил Майкрософт или создать настраиваемый набор правил в соответствии со своими нуждами. Дополнительные сведения см. в разделе [использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).

## <a name="in-source-suppression"></a>В исходном коде

Зачастую удобно указать, что предупреждение неприменимо. Это позволяет сообщить разработчику и другими лицам, которые, возможно, будут проверять код позже, что предупреждение рассмотрено и либо отложено, либо проигнорировано.

В источнике подавления предупреждений реализуется с помощью настраиваемых атрибутов. Чтобы подавить предупреждение, добавьте атрибут `SuppressMessage` в исходный код, как показано в следующем примере:

```csharp
[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Дополнительные сведения см. в разделе [подавления предупреждений с помощью атрибута SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Запуск анализа кода в рамках политики возврата

Каждая организация может предъявлять определенные требования к возвратам. В частности, может требоваться соблюдение следующих правил:

- Возвращаемый код не отсутствии ошибок сборки.

- Выполнить анализ кода в рамках последнего построения.

Этого можно достичь, задав политики возврата. Дополнительные сведения см. в разделе [улучшение качества кода с помощью политик возврата командного проекта](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Интеграция командного построения

Существует возможность использования интегрированных возможностей системы построения для запуска средства анализа в рамках процесса построения. Дополнительные сведения см. в разделе [сборок и выпусков (VSTS)](/vsts/build-release/index).

## <a name="see-also"></a>См. также

[Использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
[Как: Включение и отключение автоматического анализа кода](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
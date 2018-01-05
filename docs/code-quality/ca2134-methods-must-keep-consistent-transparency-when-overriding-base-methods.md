---
title: "CA2134: Методы должны сохранять согласованную прозрачность при переопределении базовых методов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 62438b49d91f680ae360f1d32f7cfe3b0efa2b75
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: методы должны сохранять согласованную прозрачность при переопределении базовых методов
|||  
|-|-|  
|TypeName|MethodsMustOverrideWithConsistentTransparency|  
|CheckId|CA2134|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Это правило срабатывает, если метод, помеченный атрибутом <xref:System.Security.SecurityCriticalAttribute> переопределяет метод, который является прозрачным или помечены <xref:System.Security.SecuritySafeCriticalAttribute>. Это правило также применяется, когда метод, который является прозрачным или помечены <xref:System.Security.SecuritySafeCriticalAttribute> переопределяет метод, который отмечен атрибутом <xref:System.Security.SecurityCriticalAttribute>.  
  
 Это правило применяется при переопределении виртуального метода или реализации интерфейса.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило срабатывает при попытках изменить уровень доступности метода вверх по цепочке наследования. Например, если виртуальный метод в базовом классе является прозрачным или критическим, затем производный класс должен переопределять его с прозрачный или безопасный метод. И наоборот Если виртуальный метод является критически важным для безопасности, производный класс должен переопределять его с критический метод безопасности. Это же правило применяется для реализации методов интерфейса.  
  
 Правила прозрачности применяются, когда код JIT-компиляцию, а не во время выполнения, поэтому расчет прозрачности не поддерживает динамические сведения о типе. Таким образом результат вычисления прозрачности необходимо определить исключительно из статических типов, JIT-компиляции, независимо от динамического типа.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените прозрачность метода, который переопределяет виртуальный метод или реализации интерфейса в соответствии с прозрачностью виртуального метода или метода интерфейса.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не следует отключать предупреждения из этого правила. Нарушение этого правила приведет к среде выполнения <xref:System.TypeLoadException> для сборок, использующих прозрачность уровня 2.  
  
## <a name="examples"></a>Примеры  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]  
  
## <a name="see-also"></a>См. также  
 [Прозрачный с точки зрения безопасности код, уровень 2](/dotnet/framework/misc/security-transparent-code-level-2)
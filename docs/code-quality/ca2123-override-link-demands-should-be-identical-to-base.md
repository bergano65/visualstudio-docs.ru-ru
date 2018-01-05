---
title: "CA2123: Запросы компоновки переопределения должны быть идентичны базовым | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3181e791d95f0268fd60654e8ceedb8fa394f7a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: запросы компоновки переопределения должны быть идентичны базовым
|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или защищенный метод в открытом типе переопределяет метод или реализует интерфейс и не с одинаковыми [требования связывания](/dotnet/framework/misc/link-demands) как интерфейс или виртуальный метод.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило сравнивает метод с его базовым методом (который является интерфейсом или виртуальным методом другого типа), а затем сравнивает запросы ссылок для каждого из них. Нарушение сообщается, если метод или метод базового содержит запрос компоновки, а другой — нет.  
  
 Если это правило нарушается, то вредоносный вызывающий объект может обойти запрос ссылок путем вызова небезопасного метода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, примените то же требование ссылки к переопределению метода или реализации. Если это невозможно, пометьте метод полным требованием или полностью удалить атрибут.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано различные нарушения этого правила.  
  
 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## <a name="see-also"></a>См. также  
 [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines)   
 [Требования связывания](/dotnet/framework/misc/link-demands)
---
title: 'CA1715: Идентификаторы должны иметь правильные префиксы | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8c6d744022c6be599d0df57f86c0d67b1f6a72dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: идентификаторы должны иметь правильные префиксы
|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectPrefix|  
|CheckId|CA1715|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое, если возникает в интерфейсах.<br /><br /> Не критическое — при возникновении на параметры универсального типа.|  
  
## <a name="cause"></a>Причина  
 Имя видимого снаружи интерфейса не начинается с прописных «I».  
  
 - или -  
  
 Имя параметра универсального типа в доступном типе или методе не начинается с заглавной 'T'.  
  
## <a name="rule-description"></a>Описание правила  
 По соглашению имена некоторых элементов программирования начинаются с особого префикса.  
  
 Имена интерфейсов должны начинаться с заглавной, «I» следуют другая прописная буква. Это правило сообщает о нарушениях именования имена интерфейсов, таких как «MyInterface» и «IsolatedInterface».  
  
 Имена параметров универсального типа должны начинаться с заглавной 'T' и при необходимости может следовать другая прописная буква. Данное правило сообщает нарушений для имени параметра универсального типа, такие как «V» и «Тип».  
  
 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных общеязыковая среда выполнения. Это уменьшает обучения, необходимое для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана с тем, кто имеет опыт в разработке управляемого кода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Переименуйте идентификатор, чтобы он правильно добавлен префикс.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 **В следующем примере интерфейс с неправильным именем.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]  
  
## <a name="example"></a>Пример  
 **В следующем примере предыдущее нарушение устраняется путем интерфейса префикса «I».**  
  
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]  
  
## <a name="example"></a>Пример  
 **В следующем примере показано, является параметром универсального типа с неправильным именем.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]  
  
## <a name="example"></a>Пример  
 **В следующем примере предыдущее нарушение устраняется с помощью префикса параметра универсального типа т ".**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1722: идентификаторы не должны иметь неверные префиксы](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)
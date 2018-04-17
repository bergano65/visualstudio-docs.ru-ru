---
title: 'CA1722: Идентификаторы не должны иметь неверные префиксы | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e95ef8daa7ed7fc7da4de4b99c677ef92559acb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: идентификаторы не должны иметь неверные префиксы
|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|  
|CheckId|CA1722|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Идентификатор имеет неверный префикс.  
  
## <a name="rule-description"></a>Описание правила  
 В соответствии с соглашением об именовании, только некоторые элементы программирования могут иметь имена, которые начинаются с особого префикса.  
  
 Имена типов не имеют особого префикса и не должно начинаться с «C». Это правило сообщает о нарушениях именования имена типов, например «CMyClass» и не касается нарушений имена типов, например «Кэш».  
  
 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных общеязыковая среда выполнения. Это уменьшает обучения, необходимое для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана с тем, кто имеет опыт в разработке управляемого кода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Удалите префикс от идентификатора.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1715: идентификаторы должны иметь правильные префиксы](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)
---
title: "CA2211: Неконстантные поля должны быть скрыты | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac9a04038ba1d80e8abba2efbbab19c9779c384a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: неконстантные поля должны быть скрыты
|||  
|-|-|  
|TypeName|NonConstantFieldsShouldNotBeVisible|  
|CheckId|CA2211|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или защищенный статическое поле не является константой и поддерживается только для чтения.  
  
## <a name="rule-description"></a>Описание правила  
 Для статических полей, которые не являются константными и доступными только для чтения, невозможно обеспечить потокобезопасность. Доступ к подобным полям должен тщательно контролироваться и требуются дополнительные методы программирования для синхронизации доступа к такому объекту класса. Поскольку это сложно навыками, чтобы узнать и master и тестирование такого объекта создающего свои трудности, статические поля лучше подходят для хранения данных, которые не изменяются. Это правило применяется к библиотекам; приложения не должны предоставлять все поля.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, сделайте статическое поле константой или только для чтения. Если это невозможно, измените тип, чтобы использовать альтернативный механизм, например поточно-свойство, которое управляет потокобезопасный доступ к базовому полю. Имейте в виду, что проблем, таких как конфликт блокировки и взаимоблокировки может повлиять на производительность и поведение библиотеки.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила, если вы разрабатываете приложение и поэтому имеют полный контроль над доступом к типу, содержащему статическое поле. Разработчикам библиотек не следует отключать предупреждение из этого правила; Использование статических полей неконстантное можно сделать с помощью библиотеки для разработчиков правильно использовать.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип, нарушающий это правило.  
  
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]
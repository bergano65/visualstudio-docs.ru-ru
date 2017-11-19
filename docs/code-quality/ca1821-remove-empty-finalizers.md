---
title: "CA1821: Удаляйте пустые методы завершения | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords: CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: afe1c05ff76a2b4c37296ef6a534e37a5d1229b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: удаляйте пустые методы завершения
|||  
|-|-|  
|TypeName|RemoveEmptyFinalizers|  
|CheckId|CA1821|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Тип реализует метод завершения, который является пустым, вызывает только метод завершения базового типа или вызывает только условно создаваемые методы.  
  
## <a name="rule-description"></a>Описание правила  
 Если возможно, старайтесь не использовать финализаторы, поскольку из-за отслеживания жизненного срока объектов снижается производительность программы. Сборщик мусора запустит метод завершения, прежде чем она собирает объекта. Это означает, что две коллекции необходимо, чтобы объект. Пустой метод завершения влечет за собой дополнительных издержек без никаких преимуществ.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Удалите пустой метод завершения. Если метод завершения является обязательным для отладки, заключите весь метод завершения в `#if DEBUG / #endif` директивы.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте сообщение из этого правила. Сбой для подавления финализации снижает производительность и не дает преимущества.  
  
## <a name="example"></a>Пример  
 В следующем примере показано пустой метод завершения, который должен быть удален, метод завершения, который должен быть заключен в `#if DEBUG / #endif` директивы и метод завершения, который использует `#if DEBUG / #endif` директивы правильно.  
  
 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]
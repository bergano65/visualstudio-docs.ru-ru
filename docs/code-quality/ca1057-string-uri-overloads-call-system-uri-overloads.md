---
title: "CA1057: Перегрузки строковых параметров URI вызывают перегрузки System.Uri | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: afc7f989cc8b1ff04e5b7b6207663365246b6626
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: перегрузки строковых параметров URI вызывают перегрузки System.Uri
|||  
|-|-|  
|TypeName|StringUriOverloadsCallSystemUriOverloads|  
|CheckId|CA1057|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Тип объявляет перегрузки метода, которые отличаются только заменой строкового параметра <xref:System.Uri?displayProperty=fullName> не вызывает перегрузку, которая принимает параметры и перегрузка, которая принимает строковый параметр <xref:System.Uri> параметр.  
  
## <a name="rule-description"></a>Описание правила  
 Поскольку перегрузки отличаются только по строке и<xref:System.Uri> параметра, подразумевается, что для представления универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. <xref:System.Uri> Класс предоставляет эти услуги надежным и безопасным способом. Чтобы воспользоваться преимуществами <xref:System.Uri> класса, перегруженная строка должна вызывать <xref:System.Uri> перегрузки, используя строковый аргумент.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Повторно реализовать метод, который использует строковое представление универсального кода ресурса, поэтому он создает экземпляр <xref:System.Uri> класса, используя строковый аргумент, а затем передает <xref:System.Uri> объекта перегрузку, которая имеет <xref:System.Uri> параметра.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила, если параметр строки не представляет универсальный код Ресурса.  
  
## <a name="example"></a>Пример  
 В следующем примере показано правильно реализованная строковая перегрузка.  
  
 [!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2234: передавайте объекты System.Uri вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1056: свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: возвращаемые значения URI не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
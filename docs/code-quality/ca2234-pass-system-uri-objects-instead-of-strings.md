---
title: "CA2234: Передавайте объекты System.Uri вместо строк | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fbafbcdf8750a31fc7fc7a142961e67182c4bbc7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: передавайте объекты System.Uri вместо строк
|||  
|-|-|  
|TypeName|PassSystemUriObjectsInsteadOfStrings|  
|CheckId|CA2234|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Вызов метода, имеющего строковый параметр, имя которого содержит «uri», «Uri», «urn», «Urn», «url» или «Url»; и объявляющий тип метода содержит соответствующую перегрузку метода, которая имеет <xref:System.Uri?displayProperty=fullName> параметра.  
  
## <a name="rule-description"></a>Описание правила  
 Имя параметра разделяется на лексемы, основанное на соглашении о верблюжий и затем каждый маркер проверяется на соответствие «uri», «Uri», «urn», «Urn», «url» или «Url». Если соответствие, предполагается, что параметр представляет универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. <xref:System.Uri> Класс предоставляет эти услуги надежным и безопасным способом. При наличии выбора между двумя перегрузками, которые отличаются лишь о представлениях кода URI, пользователь должен выбрать перегрузку, принимающую <xref:System.Uri> аргумент.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, вызовите перегрузку, принимающую <xref:System.Uri> аргумент.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила, если параметр строки не представляет универсальный код Ресурса.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метод `ErrorProne`, который нарушает правила и метод, `SaferWay`, правильно вызывает <xref:System.Uri> перегрузки.  
  
 [!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
 [!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
 [!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1057: перегрузки строковых параметров URI вызывают перегрузки System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)  
  
 [CA1056: свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: возвращаемые значения URI не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
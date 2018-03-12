---
title: "CA1064: Исключения должны быть открытыми | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b376de69c288a084ff3bb33aba1e1b8a0bc881e5
ms.sourcegitcommit: 3285243d6c0521266053340fe06505885d12178b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2018
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: исключения должны быть открытыми
|||  
|-|-|  
|TypeName|ExceptionsShouldBePublic|  
|CheckId|CA1064|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Исключение не являющиеся открытыми наследует непосредственно от <xref:System.Exception>, <xref:System.SystemException>, или <xref:System.ApplicationException>.  
  
## <a name="rule-description"></a>Описание правила  
 Внутреннее исключение видна только внутри своей внутренней области. После выхода исключения за пределы внутренней области для перехвата исключения можно использовать только базовое исключение. Если внутренне исключение унаследовано от <xref:System.Exception>, <xref:System.SystemException>, или <xref:System.ApplicationException>, внешний код не имеет достаточных сведений, чтобы знать, что делать с исключением.  
  
 Но если код содержит открытый исключение, которое затем используется как базовое значение для внутреннего исключения, резонно предположить, что код Далее out сможет правильно обработать базовое исключение. Открытые исключение будет содержать больше сведений, чем то, что обеспечивается <xref:System.Exception>, <xref:System.SystemException>, или <xref:System.ApplicationException>.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Сделать общедоступными исключение или извлечь внутреннего исключения из открытых исключение, которое не является <xref:System.Exception>, <xref:System.SystemException>, или <xref:System.ApplicationException>.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Предупреждения из этого правила, если вы уверены, во всех случаях, что закрытый исключение будет перехвачено внутри своей внутренней области.  
  
## <a name="example"></a>Пример  
 Это правило срабатывает в первом примере метода исключение FirstCustomException, поскольку класс исключений наследует непосредственно от Exception и является внутренним. Правило не работает в класс SecondCustomException, так как несмотря на то, что класс также наследует непосредственно от Exception, класс объявлен как открытый. Третий класс также не срабатывает правило, так как он не является производным непосредственно <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, или <xref:System.ApplicationException?displayProperty=fullName>.  
  
 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]

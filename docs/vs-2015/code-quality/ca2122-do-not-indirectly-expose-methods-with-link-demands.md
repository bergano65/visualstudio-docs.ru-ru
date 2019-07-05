---
title: CA2122. Не используйте косвенное представление методов с запросами компоновки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e0b173378194c099b2014093104f814f3454843d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687263"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122. Не используйте косвенное представление методов с требованиями ссылки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный член имеет [требования связывания](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) и вызывается членом, который не выполняет каких-либо проверок безопасности.

## <a name="rule-description"></a>Описание правила
 Запрос компоновки проверяет разрешения только непосредственно вызывающего метода. Если член `X` делает требования безопасности не вызывали ее и вызывает код защищен требованием связывания, вызывающий объект без необходимых разрешений можно использовать `X` для доступа к защищенному члену.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Добавление безопасности [данные и моделирование](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) или ссылка на элемент запросу, чтобы он больше не предоставляет незащищенный доступ к члену, защищенному запросом компоновки.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Чтобы безопасно подавить предупреждение из этого правила, необходимо убедиться в том, что ваш код не предоставлял доступ к операциям или ресурсам, которые могут использоваться в злонамеренных целях.

## <a name="example"></a>Пример
 В следующих примерах это библиотека, которая нарушает правило и приложение, демонстрирующее слабость библиотеки. Пример библиотеки содержит два метода, которые вместе нарушают правило. `EnvironmentSetting` Метод защищен требованием связывания для неограниченного доступа к переменным среды. `DomainInformation` Метод выполняет требования безопасности, не вызывающих перед вызовом `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Пример
 Следующее приложение вызывает незащищенный член библиотеки.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 В этом примере формируются следующие данные:

 **Значение из незащищенного члена: seattle.corp.contoso.com**
## <a name="see-also"></a>См. также
 [Правила написания безопасного кода](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [связывания](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [данные и моделирование](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)

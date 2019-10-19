---
title: 'CA2122: не косвенно предоставлять методы с запросами компоновки | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 099e5f3f9a09eef57ce1b888601f61e85ceb97c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643409"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: не используйте косвенное представление методов с запросами компоновки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный член имеет [запросы компоновки](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) и вызывается членом, который не выполняет проверки безопасности.

## <a name="rule-description"></a>Описание правила
 Запрос компоновки проверяет разрешения только непосредственно вызывающего метода. Если член `X` не выполняет никаких требований к безопасности вызывающих объектов и вызывает код, защищенный запросом компоновки, вызывающий объект без необходимого разрешения может использовать `X` для доступа к защищенному члену.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Добавьте данные безопасности [и моделирование](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) или требование к ссылке для члена, чтобы он больше не предохраняет незащищенный доступ к члену, защищенному с помощью запроса на подключение.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Чтобы безопасно отключить предупреждение из этого правила, необходимо убедиться, что код не предоставляет вызывающим объектам доступ к операциям или ресурсам, которые могут быть использованы необратимым образом.

## <a name="example"></a>Пример
 В следующих примерах показана библиотека, нарушающая правило, и приложение, демонстрирующее слабость библиотеки. Пример библиотеки предоставляет два метода, которые вместе нарушают правило. Метод `EnvironmentSetting` защищен запросом компоновки для неограниченного доступа к переменным среды. Метод `DomainInformation` не выполняет никаких требований безопасности вызывающих объектов перед вызовом `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Пример
 Следующее приложение вызывает незащищенный член библиотеки.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 В этом примере формируются следующие данные:

 **Значение из незащищенного члена: seattle.corp.contoso.com**
## <a name="see-also"></a>См. также раздел
 [Рекомендации по безопасному кодированию](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [требования](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) к [данным и моделированию](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)

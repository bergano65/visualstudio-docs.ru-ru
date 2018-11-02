---
title: 'CA2147: Прозрачные методы не могут использовать безопасности утверждает | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6542a2063d076cb57750015039f413b2faf4bca4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921643"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: прозрачные методы могут не использовать утверждения безопасности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Код, помеченный как <xref:System.Security.SecurityTransparentAttribute> не предоставляется разрешение на утверждение.

## <a name="rule-description"></a>Описание правила
 Это правило анализирует все методы и типы в сборке, которая является либо 100% прозрачной, либо смешанной прозрачной и критической и пометить декларативное и императивное использование <xref:System.Security.CodeAccessPermission.Assert%2A>.

 Во время выполнения, все вызовы <xref:System.Security.CodeAccessPermission.Assert%2A> из прозрачного кода приведет к <xref:System.InvalidOperationException> исключение. Это может произойти в обе сборки, прозрачные на 100%, а также в смешанных прозрачной и критической сборок, где метод или тип объявляется прозрачным, но включает декларативное и императивное Assert.

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 появилась функция с именем *прозрачности*. Отдельные методы, поля, интерфейсы, классы и типы могут быть либо прозрачный или.

 Прозрачный код не разрешено повышать уровень привилегий безопасности. Таким образом все разрешения, предоставленные или запрашиваемые автоматически передаются через код вызывающего объекта или узла домена приложения. Повышение примеры операторы Assert, требования LinkDemand, SuppressUnmanagedCode, и `unsafe` кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить эту проблему, либо пометить код, который вызывает Assert с <xref:System.Security.SecurityCriticalAttribute>, или удалить Assert.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте сообщение из этого правила.

## <a name="example"></a>Пример
 Этот код завершится ошибкой, если `SecurityTestClass` прозрачен, когда `Assert` вызывает метод <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Пример
 Один из вариантов — Просмотр кода SecurityTransparentMethod в следующем примере и, если метод считается безопасным для повышения прав, пометьте SecurityTransparentMethod с secure критически важным для этого необходимо, подробные, исчерпывающие и без ошибок безопасности аудита должна быть выполнена на метод вместе с вызовами, возникающих в рамках, чтобы метод Assert:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Другой вариант — удалить Assert из кода и разрешить все последующие файлы потока требования разрешение ввода-вывода за пределы метода SecurityTransparentMethod вызывающему. В результате проверок безопасности. В этом случае аудит безопасности не нужен, так как запросы разрешений будут переданы вызывающему объекту или домена приложения. Запросы разрешений осуществляется посредством политики безопасности, среды размещения и код разрешений.

## <a name="see-also"></a>См. также
 [Предупреждения безопасности](../code-quality/security-warnings.md)




---
title: 'CA2147: прозрачные методы могут не использовать утверждения безопасности'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f732e22d53b4d469f73c4ef3efc753240fa6841f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918101"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: прозрачные методы могут не использовать утверждения безопасности
|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Код, который помечен как <xref:System.Security.SecurityTransparentAttribute> не предоставляется достаточные для утверждения разрешения.

## <a name="rule-description"></a>Описание правила
 Это правило позволяет проанализировать все методы и типы в сборке, которая является либо 100% прозрачной, либо смешанной прозрачной и критической и пометить все декларативное и императивное использование <xref:System.Security.CodeAccessPermission.Assert%2A>.

 Во время выполнения, все вызовы <xref:System.Security.CodeAccessPermission.Assert%2A> из прозрачного кода приведет к <xref:System.InvalidOperationException> исключение. Это может происходить в обоих сборки, прозрачные на 100%, а также в смешанных сборок прозрачной и критической, где метод или тип объявляется прозрачным, но включает декларативное и императивное Assert.

 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 появилась возможность с именем *прозрачности*. Отдельные методы, поля, интерфейсы, классы и типы могут быть либо прозрачный или.

 Прозрачный код не разрешено повышать уровень привилегий безопасности. Таким образом все разрешения, предоставленные или запрашиваемые автоматически передаются через код домена приложения вызывающего объекта или узла. Повышение примеры операторы Assert, LinkDemands, SuppressUnmanagedCode, и `unsafe` кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить проблему, либо отметить код, который вызывает оператор Assert в методе с <xref:System.Security.SecurityCriticalAttribute>, или удалите оператор Assert в методе.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте сообщение из этого правила.

## <a name="example"></a>Пример
 Этот код завершится ошибкой, если `SecurityTestClass` является прозрачным, когда `Assert` вызывает исключение <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>Пример
 Один из вариантов — на проверку кода в примере ниже метод SecurityTransparentMethod и если метод считается безопасным для повышения прав, пометьте SecurityTransparentMethod с защиты с точки зрения безопасности это необходимо, подробные, полные и без ошибок безопасности вместе с вызовами, которые произойдут в течение тестируемый метод Assert в методе необходимо выполнить аудита:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

 Другой вариант — удалить Assert из кода и направить все последующие файлы потока требования разрешений ввода-вывода за пределы метода SecurityTransparentMethod вызывающему. Это позволяет проверок безопасности. В этом случае аудит безопасности не нужен, поскольку запросы разрешений будут переданы вызывающему объекту или домена приложения. Требования разрешений осуществляется посредством политики безопасности, среды размещения и предоставления разрешений на исходный код.

## <a name="see-also"></a>См. также
 [Предупреждения безопасности](../code-quality/security-warnings.md)
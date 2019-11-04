---
title: CA2114. Безопасность метода должна быть надмножеством типа | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1adc8f610644d736bc4546d8299457ba0234a1d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658674"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114. Безопасность метода должна быть надмножеством типа
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
 Тип имеет декларативную безопасность, а один из его методов имеет декларативную безопасность для того же действия безопасности, а действие безопасности не является [требованием связывания](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) или [требованиями наследования](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9), а разрешения, проверяемые этим типом, не являются подмножеством разрешения, проверенные методом.

## <a name="rule-description"></a>Описание правила
 Метод не должен иметь декларативную безопасность на уровне методов и на уровне типа для одного и того же действия. Эти две проверки не объединены; применяется только запрос уровня метода. Например, если тип требует разрешения `X`, а один из его методов требует разрешения `Y`, код не должен иметь разрешения `X` для выполнения метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Проверьте код, чтобы убедиться, что оба действия требуются. Если требуются оба действия, убедитесь, что действие уровня метода включает безопасность, указанную на уровне типа. Например, если тип требует разрешения `X`, а его метод должен также требовать разрешения `Y`, метод должен явно требовать `X` и `Y`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждений из этого правила, если метод не требует безопасности, заданной типом. Однако это не обычный сценарий, и это может указывать на необходимость тщательного анализа проектирования.

## <a name="example"></a>Пример
 В следующем примере используются разрешения среды, чтобы продемонстрировать опасности нарушения этого правила. В этом примере код приложения создает экземпляр защищенного типа, прежде чем запрещает разрешение, требуемое для типа. В реальном случае угроз приложению потребуется другой способ получения экземпляра объекта.

 В следующем примере библиотека требует разрешения на запись для типа и разрешения на чтение для метода.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Пример
 Следующий код приложения демонстрирует уязвимость библиотеки, вызывая метод, несмотря на то, что он не соответствует требованиям безопасности на уровне типа.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 В этом примере формируются следующие данные:

 ** [все разрешения] персональные данные: 6/16/1964 12:00:00 AM ** 
 ** [нет разрешение на запись (запрошено по типу)] персональные данные: 6/16/1964 12:00:00 ** 
 ** [отсутствует разрешение на чтение (затребованное методом)] не удалось получить доступ к личным сведениям: Сбой запроса. **
## <a name="see-also"></a>См. также
 [Рекомендации по безопасному написанию кода](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [требования к наследованию](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [Link Demands](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [данные и моделирование](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)

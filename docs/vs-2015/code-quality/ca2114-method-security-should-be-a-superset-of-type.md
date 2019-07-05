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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b1a360ee4ad35fd48a46f6d866912a05a584a54c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687315"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114. Безопасность метода должна быть надмножеством типа
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип имеет декларативную безопасность и один из его методов имеет декларативную безопасность для одного действия безопасности и действие по обеспечению безопасности не [требования связывания](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) или [требования наследования](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9), а также разрешения проверяемые типом не подмножество разрешений, проверяемых методом.

## <a name="rule-description"></a>Описание правила
 Метод не должен иметь тип уровня и метод декларативной безопасности для одного действия. Эти две проверки не объединяются; применяется только по требованию уровне метода. Например, если тип запрашивает разрешение `X`, и один из его методов разрешение `Y`, код не имеет разрешения `X` для выполнения метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Просмотрите код, чтобы убедиться в том, что оба действия являются обязательными. Если оба действия необходимы, убедитесь, что действие уровне метода включает безопасность, определенную на уровне типа. Например, если тип запрашивает разрешение `X`, и его метод также должен запросить разрешение `Y`, метод должен явным образом запрашивать `X` и `Y`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если метод не требует безопасности, заданную типом. Тем не менее это не обычный сценарий и может указывать на необходимость проверки тщательного планирования.

## <a name="example"></a>Пример
 В следующем примере разрешения среды для демонстрации опасности нарушения этого правила. В этом примере код приложения создает экземпляр безопасного типа перед запрет разрешений на тип. В обычном случае приложению потребуется еще один способ получения экземпляра объекта.

 В следующем примере библиотека запрашивает разрешение для типа записи и разрешения на чтение для метода.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Пример
 Следующий код приложения демонстрируется уязвимость библиотеки путем вызова метода, несмотря на то, что он не соответствует требованиям безопасности на уровне типа.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 В этом примере формируются следующие данные:

 **[Все разрешения] Личная информация: 6/16/1964 12:00:00 AM**
 **[нет разрешения на запись (затребованы тип)] персональные данные: 6/16/1964 12:00:00 AM**
 **[нет разрешение на чтение (затребованы метод)] не удалось получить доступ к личных сведений: Не удалось выполнить запрос.**
## <a name="see-also"></a>См. также
 [Правила написания безопасного кода](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [требования наследования](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [связывания](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [данные и моделирование](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)

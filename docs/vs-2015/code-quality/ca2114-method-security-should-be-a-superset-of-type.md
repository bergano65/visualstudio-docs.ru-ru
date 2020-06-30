---
title: 'CA2114: безопасность метода должна быть надмножеством типа | Документация Майкрософт'
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
ms.openlocfilehash: d7879d8b2aa9eb4ece1ce07f89681b6c0b0f5f31
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534710"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114. Безопасность метода должна быть надмножеством типа
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип имеет декларативную безопасность, а один из его методов имеет декларативную безопасность для того же действия безопасности, а действие безопасности не является [требованием связывания](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) или [требованиями наследования](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9), а разрешения, проверяемые этим типом, не являются подмножеством разрешений, проверенных методом.

## <a name="rule-description"></a>Описание правила
 Метод не должен иметь декларативную безопасность на уровне методов и на уровне типа для одного и того же действия. Эти две проверки не объединены; применяется только запрос уровня метода. Например, если тип требует разрешения `X` , а один из его методов требует разрешения `Y` , код не должен иметь разрешения `X` на выполнение метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Проверьте код, чтобы убедиться, что оба действия требуются. Если требуются оба действия, убедитесь, что действие уровня метода включает безопасность, указанную на уровне типа. Например, если тип требует разрешения `X` , а его метод должен также требовать разрешения `Y` , метод должен явно запрашивать `X` и `Y` .

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

 **[Все разрешения] персональные данные: 6/16/1964 12:00:00 AM** 
 **[Нет разрешение на запись (запрошено по типу)] персональные данные: 6/16/1964 12:00:00 AM** 
 **[Отсутствует разрешение на чтение (запрошенное методом)] не удалось получить доступ к личным сведениям: запрос не выполнен.**
## <a name="see-also"></a>См. также
 [Рекомендации по безопасному написанию кода](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [требования к наследованию](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [Link Demands](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [данные и моделирование](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)

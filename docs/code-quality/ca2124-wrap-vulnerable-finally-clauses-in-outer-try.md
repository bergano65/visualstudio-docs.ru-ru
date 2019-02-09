---
title: CA2124. Ограничьте уязвимые предложения finally во внешних блоках try
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c35a15e9ce1468edd2882396192a27a3fcc2c86
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970352"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124. Ограничьте уязвимые предложения finally во внешних блоках try

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 В версиях 1.0 и 1.1 платформы .NET Framework, содержит открытый или защищенный метод `try` / `catch` / `finally` блока. `finally` Блок сбрасывает состояние безопасности и не заключен в `finally` блока.

## <a name="rule-description"></a>Описание правила
 Это правило находит `try` / `finally` блоков в код, предназначенный для версий 1.0 и 1.1 платформы .NET Framework, могут быть раскрыты фильтры вредоносных исключений в стеке вызовов. Если конфиденциальные операции, такие как олицетворение возникает в блоке try, и возникает исключение, фильтр может быть выполнен до `finally` блока. В случае это означает, что фильтр будет выполнен от имени олицетворенного пользователя. Фильтры, в настоящее время может быть реализован только в Visual Basic.

> [!NOTE]
> В версиях 2.0 и более поздних версий .NET Framework, среда выполнения автоматически защищает `try` / `catch` /  `finally` заблокировать фильтры вредоносных исключений, если происходит сброс непосредственно в методе, содержит блок исключений.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Поместите без оболочки `try` / `finally` в внешнем блоке try. См. во втором примере ниже. Это заставляет `finally` до кода фильтра.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="pseudo-code-example"></a>Пример псевдокода

### <a name="description"></a>Описание

В приведенном ниже псевдокоде показан шаблон, обнаруживаемый этим правилом.

```csharp
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

Следующий псевдокод показан шаблон, можно использовать для защиты кода и выполнения этого правила.

```csharp
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```
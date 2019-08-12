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
ms.openlocfilehash: c75c7c240f694b18caacefc0f9b1ee07f54faf36
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920805"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124. Ограничьте уязвимые предложения finally во внешних блоках try

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
В версиях 1,0 и 1,1 .NET Framework, `try` открытый или защищенный метод содержит / `catch` / `finally` блок. Блок будет сброшен в состояние безопасности и не заключен `finally` в блок. `finally`

## <a name="rule-description"></a>Описание правила
Это правило находит `try` / вкодеблоки,предназначенныедляверсий1,0и1,1.NETFramework,которыемогутбытьуязвимыдляфильтроввредоносныхисключений,имеющихсявстекевызовов.`finally` Если конфиденциальные операции, такие как олицетворение, происходят в блоке try и создается исключение, то фильтр может выполняться перед `finally` блоком. Для примера олицетворения это означает, что фильтр будет выполняться от имени олицетворяемого пользователя. Фильтры в настоящее время реализуются только в Visual Basic.

> [!NOTE]
> В версиях 2,0 и более поздних .NET Framework среда выполнения автоматически защищает `try` / `catch` /  `finally` блок от вредоносных фильтров исключений, если сброс происходит непосредственно в методе, который содержит блок исключений.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Поместите развернутый `try` / `finally` объект во внешний блок try. См. Второй пример, приведенный ниже. Это приводит `finally` к выполнению действия до выполнения кода фильтрации.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="pseudo-code-example"></a>Пример псевдо-кода

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

В следующем псевдокоде показан шаблон, который можно использовать для защиты кода и удовлетворения этого правила.

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
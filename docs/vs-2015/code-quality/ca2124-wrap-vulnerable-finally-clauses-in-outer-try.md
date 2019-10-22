---
title: 'CA2124: Заключите уязвимые предложения finally во внешнее предложение try | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7a2a296f5dd3680209c14849b5bd863c01e6351d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660249"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: помещайте уязвимые предложения finally во внешний блок try
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 В версиях 1,0 и 1,1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] открытый или защищенный метод содержит `try` / `catch` / `finally`. Блок `finally` сбрасывает состояние безопасности и не заключается в блок `finally`.

## <a name="rule-description"></a>Описание правила
 Это правило находит `try` / `finally` блоки в коде, предназначенном для версий 1,0 и 1,1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], которые могут быть уязвимы для фильтров вредоносных исключений, имеющихся в стеке вызовов. Если конфиденциальные операции, такие как олицетворение, происходят в блоке try и создается исключение, то фильтр может выполняться перед блоком `finally`. Для примера олицетворения это означает, что фильтр будет выполняться от имени олицетворяемого пользователя. Фильтры в настоящее время реализуются только в Visual Basic.

> [!WARNING]
> В версиях 2,0 и более поздних [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] среда выполнения автоматически защищает `try` / `catch` /  `finally` блока от вредоносных фильтров исключений, если сброс происходит непосредственно в методе, содержащем блок исключения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Поместите неупакованный `try` / `finally` во внешний блок try. См. Второй пример, приведенный ниже. Это приведет к тому, что `finally` будет выполняться до фильтрации кода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="pseudo-code-example"></a>Пример псевдокода

### <a name="description"></a>Описание
 В приведенном ниже псевдокоде показан шаблон, обнаруживаемый этим правилом.

### <a name="code"></a>Код

```
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

## <a name="example"></a>Пример
 В следующем псевдокоде показан шаблон, который можно использовать для защиты кода и удовлетворения этого правила.

```
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

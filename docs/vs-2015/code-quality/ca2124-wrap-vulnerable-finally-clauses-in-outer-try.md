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
ms.openlocfilehash: 4e191ca10456f133e1213961ca2d1ed9cb8e040b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544304"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124. Ограничьте уязвимые предложения finally во внешних блоках try
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 В версиях 1,0 и 1,1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , Открытый или защищенный метод содержит `try` / `catch` / `finally` блок. `finally`Блок будет сброшен в состояние безопасности и не заключен в `finally` блок.

## <a name="rule-description"></a>Описание правила
 Это правило находит `try` / `finally` в коде блоки, предназначенные для версий 1,0 и 1,1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , которые могут быть уязвимы для фильтров вредоносных исключений, имеющихся в стеке вызовов. Если конфиденциальные операции, такие как олицетворение, происходят в блоке try и создается исключение, то фильтр может выполняться перед `finally` блоком. Для примера олицетворения это означает, что фильтр будет выполняться от имени олицетворяемого пользователя. Фильтры в настоящее время реализуются только в Visual Basic.

> [!WARNING]
> В версиях 2,0 и более поздних версий [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Среда выполнения автоматически защищает `try` / `catch` /  `finally` блок от вредоносных фильтров исключений, если сброс происходит непосредственно в методе, содержащем блок исключения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Поместите развернутый объект `try` / `finally` во внешний блок try. См. Второй пример, приведенный ниже. Это приводит `finally` к выполнению действия до выполнения кода фильтрации.

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

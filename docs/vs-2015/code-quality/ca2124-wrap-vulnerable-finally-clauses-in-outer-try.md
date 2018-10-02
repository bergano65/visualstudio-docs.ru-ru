---
title: 'CA2124: Помещайте уязвимые предложения finally во внешний блок try | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5af65dce5e809a32174ca6706c7ac8072cc4c318
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591961"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: помещайте уязвимые предложения finally во внешний блок try
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2124: Помещайте уязвимые предложения finally во внешний блок try](https://docs.microsoft.com/visualstudio/code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try).

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 В версиях 1.0 и 1.1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], содержит открытый или защищенный метод `try` / `catch` / `finally` блока. `finally` Блок сбрасывает состояние безопасности и не заключен в `finally` блока.

## <a name="rule-description"></a>Описание правила
 Это правило находит `try` / `finally` блоков в код, предназначенный для версий 1.0 и 1.1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , могут быть раскрыты фильтры вредоносных исключений в стеке вызовов. Если конфиденциальные операции, такие как олицетворение возникает в блоке try, и возникает исключение, фильтр может быть выполнен до `finally` блока. В случае это означает, что фильтр будет выполнен от имени олицетворенного пользователя. Фильтры, в настоящее время может быть реализован только в Visual Basic.

> [!WARNING]
>  **Примечание** в версиях 2.0 и более поздних версий [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], среда выполнения автоматически защищает `try` / `catch` /  `finally` заблокировать фильтры вредоносных исключений, если происходит сброс непосредственно в метод, содержащий блок исключений.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Поместите без оболочки `try` / `finally` в внешнем блоке try. См. во втором примере ниже. Это заставляет `finally` до кода фильтра.

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
 Следующий псевдокод показан шаблон, можно использовать для защиты кода и выполнения этого правила.

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




---
title: 'CA2124: помещайте уязвимые предложения finally во внешний блок try'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c299652e779476f2936c193a8bdb646e7b655dd4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: помещайте уязвимые предложения finally во внешний блок try
|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 В версиях 1.0 и 1.1 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], содержит открытый или защищенный метод `try` / `catch` / `finally` блока. `finally` Блок сбрасывает состояние безопасности и не заключен в `finally` блока.

## <a name="rule-description"></a>Описание правила
 Это правило находит `try` / `finally` блоков в код, предназначенный для версии 1.0 и 1.1 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , может стать уязвимым для фильтров вредоносных исключений присутствуют в стеке вызовов. Если важные операции, такие как олицетворение возникает в блоке try, и возникает исключение, фильтр может быть выполнен до `finally` блока. В случае это означает, что фильтр будет выполнен от имени олицетворенного пользователя. Фильтры добавляются в настоящее время может быть реализован только в Visual Basic.

> [!WARNING]
>  **Примечание** в версиях 2.0 и более поздних версиях [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], среда выполнения автоматически защищает `try` / `catch` /  `finally` запретить фильтры вредоносных исключение в случае сброса непосредственно в методе, который содержит блок исключений.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Поместите оболочку `try` / `finally` в внешнем блоке try. См. в следующем примере. Это заставляет `finally` для выполнения перед кодом фильтра.

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
 Ниже псевдокоде показан шаблон, можно использовать для защиты кода и выполнения этого правила.

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
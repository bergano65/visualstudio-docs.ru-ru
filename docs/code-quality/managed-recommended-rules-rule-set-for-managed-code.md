---
title: Набор правил "Рекомендуемые правила для управляемого кода"
ms.date: 11/04/2016
description: Сведения о наборе правил "управляемые Рекомендуемые правила" в Visual Studio. Ознакомьтесь с описанием правил, которые касаются безопасности, надежности и других критических проблем.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 30874b00f7bca4d66a60e359445c28be686d3269
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435369"
---
# <a name="managed-recommended-rules-rule-set-for-managed-code"></a>Набор правил "Рекомендуемые правила для управляемого кода"

Используйте набор правил "Рекомендуемые правила Майкрософт", чтобы сосредоточиться на наиболее важных проблемах в управляемом коде, включая потенциальные бреши в системе безопасности, сбои приложений, а также другие важные логики и ошибки проектирования. Этот набор правил включает все правила из набора правил " [управляемые минимальные правила](managed-minimum-rules-rule-set-for-managed-code.md) ".

Включите это правило в набор настраиваемых правил, создаваемых для проектов.

|Правило|Описание|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|
|[CA1009](../code-quality/ca1009.md)|Правильно объявляйте обработчики событий|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Пометьте сборки с помощью AssemblyVersionAttribute|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Методы интерфейса должны быть доступны для вызова дочерними типами|
|[CA1049](../code-quality/ca1049.md)|Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|Переместите методы P/Invoke в класс NativeMethods|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Не скрывайте методы базовых классов|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|Правильно реализуйте IDisposable|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Не вызывайте исключения в непредвиденных местах|
|[CA1301](../code-quality/ca1301.md)|Избегайте повторяющихся акселераторов|
|[CA1400](../code-quality/ca1400.md)|Для методов P/Invoke должны существовать точки входа|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|Методы P/Invoke не должны быть видимыми|
|[CA1403](../code-quality/ca1403.md)|Типы с автомакетом не должны быть видимыми для COM|
|[CA1404](../code-quality/ca1404.md)|Вызывайте GetLastError сразу после P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Базовые типы, относящиеся к типу, видимому для COM, должны быть видимыми для COM|
|[CA1410](../code-quality/ca1410.md)|Методы регистрации COM должны быть согласованными|
|[CA1415](../code-quality/ca1415.md)|Правильно объявляйте методы P/Invoke|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Удалите пустые методы завершения|
|[CA1900](../code-quality/ca1900.md)|Поля типов значений должны быть переносимыми|
|[CA1901](../code-quality/ca1901.md)|Объявления P/Invoke должны быть переносимыми|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|Не блокируйте объекты с ненадежными удостоверениями|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Проверьте запросы SQL на наличие уязвимостей системы безопасности|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Укажите тип маршалинга для строковых аргументов P/Invoke|
|[CA2108](../code-quality/ca2108.md)|Проверьте объявляемые параметры безопасности типов значений|
|[CA2111](../code-quality/ca2111.md)|Указатели не должны быть видимыми|
|[CA2112](../code-quality/ca2112.md)|Защищенные типы не должны предоставлять поля|
|[CA2114](../code-quality/ca2114.md)|Безопасность метода должна быть надмножеством типа|
|[CA2116](../code-quality/ca2116.md)|APTCA-методы должны вызывать только APTCA-методы|
|[CA2117](../code-quality/ca2117.md)|APTCA-типы должны расширять только базовые APTCA-типы|
|[CA2122](../code-quality/ca2122.md)|Не используйте косвенное представление методов с требованиями ссылки|
|[CA2123](../code-quality/ca2123.md)|Переопределяющие требования ссылки должны быть идентичны базовым|
|[CA2124](../code-quality/ca2124.md)|Ограничьте уязвимые предложения finally во внешних блоках try|
|[CA2126](../code-quality/ca2126.md)|Для требований ссылок на тип необходимы требования наследования|
|[CA2131](../code-quality/ca2131.md)|Критические для безопасности типы не могут участвовать в эквивалентности типов|
|[CA2132](../code-quality/ca2132.md)|Конструкторы по умолчанию должны быть по меньшей мере такими же критическими, как конструкторы по умолчанию базового типа|
|[CA2133](../code-quality/ca2133.md)|Делегаты должны быть привязаны к методам с соответствующей прозрачностью|
|[CA2134](../code-quality/ca2134.md)|Методы должны сохранять одинаковую прозрачность при переопределении базовых методов|
|[CA2137](../code-quality/ca2137.md)|Прозрачные методы должны содержать только поддающийся проверке промежуточный язык|
|[CA2138](../code-quality/ca2138.md)|Прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140.md)|Прозрачный код не должен ссылаться на критические для безопасности элементы|
|[CA2141](../code-quality/ca2141.md)|Прозрачные методы не должны соответствовать требованиям LinkDemand|
|[CA2146](../code-quality/ca2146.md)|Типы должны быть по крайней мере настолько же критическими, как их базовые типы и интерфейсы|
|[CA2147](../code-quality/ca2147.md)|Прозрачные методы могут не использовать утверждения безопасности|
|[CA2149](../code-quality/ca2149.md)|Прозрачные методы не должны вызывать машинный код|
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|Повторно порождайте исключения для сохранения сведений стека|
|[CA2202](../code-quality/ca2202.md)|Не ликвидируйте объекты несколько раз|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Используйте встроенную инициализацию статических полей типов значений|
|[CA2212](../code-quality/ca2212.md)|Не помечайте обслуживаемые компоненты с помощью WebMethod|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Следует высвобождать высвобождаемые поля|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|Не вызывайте переопределяемые методы в конструкторах|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Высвобождаемые типы должны объявлять методы завершения|
|[CA2220](../code-quality/ca2220.md)|Методы завершения должны вызывать метод завершения базового класса|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Реализуйте конструкторы сериализации|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Перегрузите оператор равенства на переопределяющем типе ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Отметьте точки входа Windows Forms меткой STAThread|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Пометьте все несериализуемые поля|
|[CA2236](../code-quality/ca2236.md)|Вызывайте методы базового класса для типов ISerializable|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|Пометьте типы ISerializable атрибутом SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Правильно реализуйте методы сериализации|
|[CA2240](../code-quality/ca2240.md)|Правильно реализуйте ISerializable|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Задайте правильные аргументы для методов форматирования|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Правильно выполняйте проверку NaN|

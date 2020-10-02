---
title: Набор правил "Правила безопасности" для управляемого кода
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f3205bf3c81bbb9dac19c810e3a89a5fcd2227b
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658403"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Набор правил "Правила безопасности" для управляемого кода

Используйте правило Microsoft Security Rules, установленное для устаревшего анализа кода, чтобы максимально увеличить количество потенциальных проблем безопасности, о которых сообщается.

|Правило|Описание|
|----------|-----------------|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Проверьте запросы SQL на наличие уязвимостей системы безопасности|
|[CA2102](../code-quality/ca2102.md)|Перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков|
|[CA2103](../code-quality/ca2103.md)|Проверьте принудительную безопасность|
|[CA2104](../code-quality/ca2104.md)|Не объявляйте изменяющиеся ссылочные типы только для чтения|
|[CA2105](../code-quality/ca2105.md)|Поля массивов не должны быть доступны только для чтения|
|[CA2106](../code-quality/ca2106.md)|Обеспечьте безопасность утверждений|
|[CA2107](../code-quality/ca2107.md)|Проверьте использование Deny и Permit Only|
|[CA2108](../code-quality/ca2108.md)|Проверьте объявляемые параметры безопасности типов значений|
|[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109)|Проверьте видимые обработчики событий|
|[CA2111](../code-quality/ca2111.md)|Указатели не должны быть видимыми|
|[CA2112](../code-quality/ca2112.md)|Защищенные типы не должны предоставлять поля|
|[CA2114](../code-quality/ca2114.md)|Безопасность метода должна быть надмножеством типа|
|[CA2115](../code-quality/ca2115.md)|Вызывайте GC.KeepAlive при использовании собственных ресурсов|
|[CA2116](../code-quality/ca2116.md)|APTCA-методы должны вызывать только APTCA-методы|
|[CA2117](../code-quality/ca2117.md)|APTCA-типы должны расширять только базовые APTCA-типы|
|[CA2118](../code-quality/ca2118.md)|Проверьте использование атрибута SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Запечатайте методы, соответствующие частным интерфейсам|
|[CA2120](../code-quality/ca2120.md)|Обеспечьте безопасность конструкторов сериализации|
|[CA2121](../code-quality/ca2121.md)|Статические конструкторы должны быть частными|
|[CA2122](../code-quality/ca2122.md)|Не используйте косвенное представление методов с требованиями ссылки|
|[CA2123](../code-quality/ca2123.md)|Переопределяющие требования ссылки должны быть идентичны базовым|
|[CA2124](../code-quality/ca2124.md)|Ограничьте уязвимые предложения finally во внешних блоках try|
|[CA2126](../code-quality/ca2126.md)|Для требований ссылок на тип необходимы требования наследования|
|[CA2130](../code-quality/ca2130.md)|Важные константы безопасности должны быть прозрачными|
|[CA2131](../code-quality/ca2131.md)|Критические для безопасности типы не могут участвовать в эквивалентности типов|
|[CA2132](../code-quality/ca2132.md)|Конструкторы по умолчанию должны быть по меньшей мере такими же критическими, как конструкторы по умолчанию базового типа|
|[CA2133](../code-quality/ca2133.md)|Делегаты должны быть привязаны к методам с соответствующей прозрачностью|
|[CA2134](../code-quality/ca2134.md)|Методы должны сохранять одинаковую прозрачность при переопределении базовых методов|
|[CA2135](../code-quality/ca2135.md)|Сборки уровня 2 не должны содержать LinkDemands|
|[CA2136](../code-quality/ca2136.md)|Члены не должны иметь противоречащие заметки прозрачности|
|[CA2137](../code-quality/ca2137.md)|Прозрачные методы должны содержать только поддающийся проверке промежуточный язык|
|[CA2138](../code-quality/ca2138.md)|Прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity|
|[CA2139](../code-quality/ca2139.md)|Прозрачные методы могут не использовать атрибут HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140.md)|Прозрачный код не должен ссылаться на критические для безопасности элементы|
|[CA2141](../code-quality/ca2141.md)|Прозрачные методы не должны соответствовать требованиям LinkDemand|
|[CA2142](../code-quality/ca2142.md)|Прозрачный код не должен быть защищен проверками LinkDemands|
|[CA2143](../code-quality/ca2143.md)|Прозрачные методы не должны использовать требования безопасности|
|[CA2144](../code-quality/ca2144.md)|Прозрачный код не должен выполнять загрузку сборок из массивов байтов|
|[CA2145](../code-quality/ca2145.md)|Прозрачные методы не должны быть отмечены атрибутом SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146.md)|Типы должны быть по крайней мере настолько же критическими, как их базовые типы и интерфейсы|
|[CA2147](../code-quality/ca2147.md)|Прозрачные методы могут не использовать утверждения безопасности|
|[CA2149](../code-quality/ca2149.md)|Прозрачные методы не должны вызывать машинный код|
|[CA2210](../code-quality/ca2210.md)|Сборки должны иметь допустимые строгие имена|
|[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300)|Не используйте небезопасный десериализатор BinaryFormatter|
|[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301)|Не вызывайте BinaryFormatter.Deserialize, не задав предварительно BinaryFormatter.Binder|
|[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302)|Убедитесь, что BinaryFormatter.Binder задан перед вызовом BinaryFormatter.Deserialize|
|[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305)|Не используйте небезопасный десериализатор LosFormatter|
|[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310)|Не используйте небезопасный десериализатор NetDataContractSerializer|
|[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311)|Не десериализируйте, не задав предварительно NetDataContractSerializer.Binder|
|[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312)|Убедитесь, что NetDataContractSerializer.Binder задан перед десериализацией|
|[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315)|Не используйте небезопасный десериализатор ObjectStateFormatter|
|[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321)|Не десериализируйте с помощью JavaScriptSerializer, используя SimpleTypeResolver|
|[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322)|Убедитесь, что JavaScriptSerializer не был инициализирован с помощью SimpleTypeResolver до десериализации|
|[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001)|Проверьте код на наличие уязвимостей к внедрению кода SQL|
|[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002)|Проверьте код на наличие уязвимостей к межсайтовым сценариям (XSS)|
|[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003)|Проверьте код на наличие уязвимостей к внедрению пути к файлу|
|[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004)|Проверьте код на наличие уязвимостей к раскрытию информации|
|[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005)|Проверьте код на наличие уязвимостей к внедрению LDAP|
|[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006)|Проверьте код на наличие уязвимостей к внедрению команд процесса|
|[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007)|Проверьте код на наличие уязвимостей к открытому перенаправлению|
|[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008)|Проверьте код на наличие уязвимостей к внедрению кода XPath|
|[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009)|Проверьте код на наличие уязвимостей к внедрению кода XML|
|[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010)|Проверьте код на наличие уязвимостей к внедрению кода XAML|
|[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011)|Проверьте код на наличие уязвимостей к внедрению DLL|
|[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012)|Проверьте код на наличие уязвимостей к внедрению регулярных выражений|
|[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358)|Не используйте небезопасные режимы шифрования|
|[CA5403](/dotnet/fundamentals/code-analysis/quality-rules/ca5403)|Не используйте жестко заданный сертификат|
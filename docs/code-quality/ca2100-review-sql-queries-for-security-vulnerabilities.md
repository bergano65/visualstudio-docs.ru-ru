---
title: CA2100. Проверьте запросы SQL на наличие уязвимостей системы безопасности
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 26e4b1c291c536597f699bd57cc11c041c3b168b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939287"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100. Проверьте запросы SQL на наличие уязвимостей системы безопасности

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Задает метод <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> свойства с помощью строки, составленное из строкового аргумента метода.

## <a name="rule-description"></a>Описание правила

Это правило предполагает, что строковый аргумент содержит введенные пользователем данные. Созданная из введенных пользователем данных командная строка SQL уязвима перед атаками путем внедрения кода SQL. Атаки путем внедрения кода SQL пользователь-злоумышленник вводит данные, которые изменяют структуру запроса при попытке привести к повреждению или получения несанкционированного доступа к базе данных. Типичные методы включают внедрение одинарная кавычка или апостроф, который является разделитель строк-литералов SQL; два тире, обозначающих Комментарий SQL; Используйте точку с запятой, который указывает, что соответствует новой команды. Если входные данные пользователя должны быть частью запроса, используйте один из следующих, перечислены в порядке эффективности, чтобы снизить риск атаки.

- Используйте хранимую процедуру.

- Использование параметризованной командой строки.

- Проверьте входные данные пользователя для типа и содержимое, прежде чем построить строку команды.

Следующие типы .NET Framework реализуют <xref:System.Data.IDbCommand.CommandText%2A> свойство или конструкторы, свойства с помощью строкового аргумента.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> и <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> и <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> и <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> и <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

Обратите внимание на то, что это правило нарушается при использовании метода ToString типа явно или неявно для создания строки запроса. Пример.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 Правило нарушается, так как пользователь-злоумышленник может переопределить метод ToString().

 Правило также нарушается, если метод ToString используется неявно.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, используйте параметризованный запрос.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если текст команды не содержит вводимых пользователем.

## <a name="example"></a>Пример
 В примере показан метод, `UnsafeQuery`, который нарушает правило и метод, `SaferQuery`, выполняет правила, используя строку параметризованные команды.

 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]

## <a name="see-also"></a>См. также
 [Общие сведения о безопасности](/dotnet/framework/data/adonet/security-overview)
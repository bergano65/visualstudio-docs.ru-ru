---
title: CA2100. Проверьте запросы SQL на наличие уязвимостей системы безопасности
ms.date: 11/04/2016
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
ms.openlocfilehash: 837abb051467135b6332b53b2c59e5016d3adff6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233066"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100. Проверьте запросы SQL на наличие уязвимостей системы безопасности

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Метод задает <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> свойство, используя строку, созданную из строкового аргумента в метод.

## <a name="rule-description"></a>Описание правила

Это правило предполагает, что строковый аргумент содержит введенные пользователем данные. Созданная из введенных пользователем данных командная строка SQL уязвима перед атаками путем внедрения кода SQL. При атаке путем внедрения кода SQL злонамеренный пользователь предоставляет входные данные, которые изменяют структуру запроса при попытке повредить или получить несанкционированный доступ к основной базе данных. Типичные методы включают в себя введение одинарной кавычки или апострофа, который является разделителем строкового литерала SQL; два тире, обозначающие комментарий SQL; и точка с запятой, которая указывает, что следует Новая команда. Если входные данные пользователя должны быть частью запроса, используйте один из следующих элементов, перечисленных в порядке эффективности, чтобы снизить риск атаки.

- Используйте хранимую процедуру.

- Используйте параметризованную командную строку.

- Перед построением строки команды проверьте введенные пользователем данные как для типа, так и для содержимого.

Следующие типы .NET реализуют <xref:System.Data.IDbCommand.CommandText%2A> свойство или предоставляют конструкторы, которые устанавливают свойство с помощью строкового аргумента.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> и <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> и <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> и <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> и <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

Обратите внимание, что это правило нарушается, если метод ToString типа используется явно или неявно для создания строки запроса. Пример.

```csharp
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

Правило нарушается, так как пользователь-злоумышленник может переопределить метод ToString ().

Правило также нарушается, когда ToString используется неявно.

```csharp
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, используйте параметризованный запрос.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Можно отключить вывод предупреждения из этого правила, если текст команды не содержит вводимых пользователем данных.

## <a name="example"></a>Пример

В следующем примере показан метод, `UnsafeQuery`, который нарушает правило и `SaferQuery`метод, который удовлетворяет правилу с помощью параметризованной командной строки.

[!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
[!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
[!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]

## <a name="see-also"></a>См. также

- [Общие сведения о безопасности](/dotnet/framework/data/adonet/security-overview)
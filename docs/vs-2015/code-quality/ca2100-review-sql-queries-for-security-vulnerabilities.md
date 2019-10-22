---
title: 'CA2100: Ознакомьтесь с запросами SQL для уязвимости системы безопасности | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e7258ec98937e7ea84773e788234e5a34772e9d4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652195"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: проанализируйте SQL-запросы с целью выявления уязвимостей безопасности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод задает свойство <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName>, используя строку, созданную из строкового аргумента в метод.

## <a name="rule-description"></a>Описание правила
 Это правило предполагает, что строковый аргумент содержит введенные пользователем данные. Созданная из введенных пользователем данных командная строка SQL уязвима перед атаками путем внедрения кода SQL. При атаке путем внедрения кода SQL злонамеренный пользователь предоставляет входные данные, которые изменяют структуру запроса при попытке повредить или получить несанкционированный доступ к основной базе данных. Типичные методы включают в себя введение одинарной кавычки или апострофа, который является разделителем строкового литерала SQL; два тире, обозначающие комментарий SQL; и точка с запятой, которая указывает, что следует Новая команда. Если входные данные пользователя должны быть частью запроса, используйте один из следующих элементов, перечисленных в порядке эффективности, чтобы снизить риск атаки.

- Используйте хранимую процедуру.

- Используйте параметризованную командную строку.

- Перед построением строки команды проверьте введенные пользователем данные как для типа, так и для содержимого.

  Следующие типы [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] реализуют свойство <xref:System.Data.IDbCommand.CommandText%2A> или предоставляют конструкторы, которые устанавливают свойство с помощью строкового аргумента.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> и <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>.

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> и <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>.

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> и <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>.

- [System. Data. SqlServerCe. Склцекомманд] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) и [System. Data. SqlServerCe. Склцедатаадаптер] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> и <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>.

  Обратите внимание, что это правило нарушается, если метод ToString типа используется явно или неявно для создания строки запроса. Пример.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 Правило нарушается, так как пользователь-злоумышленник может переопределить метод ToString ().

 Правило также нарушается, когда ToString используется неявно.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, используйте параметризованный запрос.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если текст команды не содержит вводимых пользователем данных.

## <a name="example"></a>Пример
 В следующем примере показан метод `UnsafeQuery`, нарушающий правило, и метод `SaferQuery`, который удовлетворяет правилу с помощью параметризованной командной строки.

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>См. также раздел
 [Общие сведения о безопасности](https://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)

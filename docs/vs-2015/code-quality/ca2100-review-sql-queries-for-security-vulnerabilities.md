---
title: 'CA2100: Проверьте SQL-запросы для уязвимости системы безопасности | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7d39d324942348050d05dfb5273a9b4075747b1c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206509"
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
 Задает метод <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> свойства с помощью строки, составленное из строкового аргумента метода.

## <a name="rule-description"></a>Описание правила
 Это правило предполагает, что строковый аргумент содержит введенные пользователем данные. Созданная из введенных пользователем данных командная строка SQL уязвима перед атаками путем внедрения кода SQL. Атаки путем внедрения кода SQL пользователь-злоумышленник вводит данные, которые изменяют структуру запроса при попытке привести к повреждению или получения несанкционированного доступа к базе данных. Типичные методы включают внедрение одинарная кавычка или апостроф, который является разделитель строк-литералов SQL; два тире, обозначающих Комментарий SQL; Используйте точку с запятой, который указывает, что соответствует новой команды. Если входные данные пользователя должны быть частью запроса, используйте один из следующих, перечислены в порядке эффективности, чтобы снизить риск атаки.

-   Используйте хранимую процедуру.

-   Использование параметризованной командой строки.

-   Проверьте входные данные пользователя для типа и содержимое, прежде чем построить строку команды.

 Следующие [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] типы реализуют <xref:System.Data.IDbCommand.CommandText%2A> свойство или конструкторы, свойства с помощью строкового аргумента.

-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> и <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> и <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> и <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

-   [System.Data.SqlServerCe.SqlCeCommand] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) и [System.Data.SqlServerCe.SqlCeDataAdapter] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> и <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

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

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>См. также
 [Общие сведения о безопасности](http://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)




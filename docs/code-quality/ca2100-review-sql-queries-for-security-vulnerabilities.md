---
title: "CA2100: проанализируйте SQL-запросы с целью выявления уязвимостей безопасности | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Review SQL queries for security vulnerabilities"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
  - "CA2100"
helpviewer_keywords: 
  - "CA2100"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2100: проанализируйте SQL-запросы с целью выявления уязвимостей безопасности
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|  
|CheckId|CA2100|  
|Категория|Microsoft.Security|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Метод задает свойство <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> с использованием строки, созданной для метода из строкового аргумента.  
  
## Описание правила  
 Это правило предполагает, что строковый аргумент содержит введенные пользователем данные.  Созданная из введенных пользователем данных командная строка SQL уязвима перед атаками путем внедрения кода SQL.  При атаке путем внедрения кода SQL пользователь\-злоумышленник вводит данные, которые изменяют структуру запроса, пытаясь повредить используемую базу данных или получить несанкционированный доступ к ней.  Среди распространенных способов можно назвать вставку кавычки или апострофа, т. е. литерального разделителя строки в SQL; двух тире, обозначающих комментарий SQL; и точки с запятой, обозначающей, что далее последует новая команда.  Если вводимые пользователем данные должны присутствовать в запросе, следует использовать перечисленные ниже в порядке эффективности методы, чтобы уменьшить риск атаки.  
  
-   Используйте хранимую процедуру.  
  
-   Используйте параметризованную командную строку.  
  
-   Проверяйте тип и содержимое вводимых пользователем данных, прежде чем создавать командную строку.  
  
 Следующие типы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] реализуют свойство <xref:System.Data.IDbCommand.CommandText%2A> или предоставляют конструкторы, которые задают это свойство с использованием строкового аргумента.  
  
-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> и <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>.  
  
-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> и <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>.  
  
-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> и <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>.  
  
-   [System.Data.SqlServerCe.SqlCeCommand](assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&autoUpgrade=True) и [System.Data.SqlServerCe.SqlCeDataAdapter](assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&autoUpgrade=True)  
  
-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> и <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>.  
  
 Следует отметить, что это правило нарушается, когда для построения строки запроса явно или неявно используется метод типа ToString.  Пример.  
  
```  
int x = 10;  
string query = "SELECT TOP " + x.ToString() + " FROM Table";  
```  
  
 Это правило нарушается, так как злонамеренный пользователь может переопределить метод ToString\(\).  
  
 Правило также нарушается, если метод ToString используется неявно.  
  
```  
int x = 10;  
string query = String.Format("SELECT TOP {0} FROM Table", x);  
```  
  
## Устранение нарушений  
 Чтобы исправить нарушение этого правила, используйте параметризованный запрос.  
  
## Отключение предупреждений  
 Если текст команды не содержит вводимых пользователем данных, для данного правила можно отключить вывод предупреждений.  
  
## Пример  
 В следующем примере показан метод `UnsafeQuery`, нарушающий правило, и метод `SaferQuery`, удовлетворяющий правилу благодаря использованию параметризованной командной строки.  
  
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-cs[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]  
  
## См. также  
 [Общие сведения о безопасности](../Topic/Security%20Overview2.md)
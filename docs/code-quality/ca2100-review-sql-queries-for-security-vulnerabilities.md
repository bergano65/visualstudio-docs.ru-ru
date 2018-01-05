---
title: "CA2100: Проверьте SQL-запросов для уязвимостей системы безопасности | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 06d214a8726ea03cc16aff8391db1acceb3f91f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: проанализируйте SQL-запросы с целью выявления уязвимостей безопасности
|||  
|-|-|  
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|  
|CheckId|CA2100|  
|Категория|Microsoft.Security|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Метод задает <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> свойства с использованием строки, созданной из строкового аргумента метода.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило предполагает, что строковый аргумент содержит введенные пользователем данные. Созданная из введенных пользователем данных командная строка SQL уязвима перед атаками путем внедрения кода SQL. При атаке путем внедрения кода SQL пользователь-злоумышленник вводит данные, которые изменяют структуру запроса при попытке привести к повреждению или получить несанкционированный доступ к базе данных. Типичные приемы можно назвать вставку кавычки или апострофа, который является разделитель строк-литералов SQL; двух тире, обозначающих Комментарий SQL; и точкой с запятой, которое указывает, соответствует новую команду. Если входные данные пользователя должны быть частью запроса, воспользуйтесь одним из следующих значений, перечисленных в порядке эффективности методы, чтобы снизить риск атак.  
  
-   Используйте хранимую процедуру.  
  
-   Использование параметризованной командной строки.  
  
-   Проверка введенных пользователем данных тип и содержимое перед построением командную строку.  
  
 Следующие [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] типы реализуют <xref:System.Data.IDbCommand.CommandText%2A> свойство или предоставляют конструкторы, которые свойству, используя строковый аргумент.  
  
-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> и <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>.  
  
-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> и <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>.  
  
-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> и <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>.  
  
-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> и <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>.  
  
 Обратите внимание, что это правило нарушается, при использовании метода ToString типа явно или неявно для построения строки запроса. Пример.  
  
```  
int x = 10;  
string query = "SELECT TOP " + x.ToString() + " FROM Table";  
```  
  
 При нарушении правила, так как пользователь-злоумышленник может переопределить метод ToString().  
  
 Также при нарушении правила при ToString используется неявно.  
  
```  
int x = 10;  
string query = String.Format("SELECT TOP {0} FROM Table", x);  
```  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, используйте параметризованный запрос.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, если текст команды не содержит вводимых пользователем.  
  
## <a name="example"></a>Пример  
 В примере показан метод, `UnsafeQuery`, которое нарушает правило и метод, `SaferQuery`, соответствующий этому правилу, используя строку параметризованной команды.  
  
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о безопасности](/dotnet/framework/data/adonet/security-overview)
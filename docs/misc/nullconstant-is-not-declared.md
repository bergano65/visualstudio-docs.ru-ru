---
title: "Нет объявления для: &quot;&lt;константа_null&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30822"
  - "vbc30822"
helpviewer_keywords: 
  - "BC30822"
ms.assetid: dda0e2c1-46a3-4cc4-b36c-0858a5259bac
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Нет объявления для: &quot;&lt;константа_null&gt;&quot;
Нет объявления для: "\<константа\_null\>". Константа Null больше не поддерживается; используйте System.DBNull.  
  
 В операторе используется ключевое слово `Null`, которое больше не поддерживается в Visual Basic.  
  
 **Идентификатор ошибки:** BC30822  
  
### Исправление ошибки  
  
1.  Используйте <xref:System.DBNull> вместо `Null`. В следующем примере это показано.  
  
    ```  
    Sub TestDBNull() Dim t As DataTable ' Assume the DataGrid is bound to a DataTable. t = CType(DataGrid1.DataSource, DataTable) Dim r As DataRow r = t.Rows(datagrid1.CurrentCell.RowNumber) r.BeginEdit r(1) = System.DBNull.Value ' Assign DBNull to the record. r.EndEdit r.AcceptChanges If r.IsNull(1) Then MsgBox("") End If End Sub  
    ```  
  
2.  Используйте ключевое слово [Nothing](/dotnet/visual-basic/language-reference/nothing) в операторах присваивания и сравнения, в которых участвуют объектные переменные. В следующем примере это показано.  
  
    ```  
    Sub TestNothing() Dim cls As Object ' cls is Nothing if it has not been assigned using the New keyword. If (cls Is Nothing) Then MsgBox("cls is Nothing") End If cls = Nothing ' Assign Nothing to the class variable cls. End Sub  
    ```  
  
## См. также  
 <xref:System.DBNull>   
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [Programming Element Support Changes Summary](http://msdn.microsoft.com/ru-ru/0483590a-6309-449c-a2fa-effa26a03b95)
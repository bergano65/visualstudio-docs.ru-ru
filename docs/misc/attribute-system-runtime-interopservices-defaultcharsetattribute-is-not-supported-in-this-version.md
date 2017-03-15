---
title: "Атрибут &quot;System.Runtime.InteropServices.DefaultCharSetAttribute&quot; не поддерживается в данной версии. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32510"
  - "vbc32510"
helpviewer_keywords: 
  - "BC32510"
ms.assetid: e2eec233-6e0b-4f2f-a801-b0274e579c0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Атрибут &quot;System.Runtime.InteropServices.DefaultCharSetAttribute&quot; не поддерживается в данной версии.
Атрибут <xref:System.Runtime.InteropServices.DefaultCharSetAttribute?displayProperty=fullName> позволяет задать кодировку, используемую для маршалируемых строк. Его значением является член перечисления <xref:System.Runtime.InteropServices.CharSet?displayProperty=fullName>.  
  
 В текущей версии [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] этот атрибут не поддерживается. Возможно, он будет поддерживаться в следующих версиях.  
  
 **Идентификатор ошибки:** BC32510  
  
### Исправление ошибки  
  
-   Используйте [Оператор Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) для задания кодировки для каждой объявляемой внешней процедуры. Это показано в следующем примере.  
  
    ```  
    Ansi Declare Function GetUserName Lib "advapi32.dll" _ (ByVal lpBuffer As String, ByRef nSize As Integer) As Integer Unicode Declare Sub externalProc Lib "projectlib.dll" _ (ByVal arg As Double)  
    ```  
  
     Если в операторе `Declare` не указана кодировка, то по умолчанию используется кодировка ANSI.  
  
## См. также  
 <xref:System.Runtime.InteropServices.DefaultCharSetAttribute>   
 <xref:System.Runtime.InteropServices.CharSet>   
 [НЕ В СБОРКЕ. Атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Оператор Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)
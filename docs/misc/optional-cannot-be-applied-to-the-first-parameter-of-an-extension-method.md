---
title: "&quot;Optional&quot; не может применяться к первому параметру метода расширения | Microsoft Docs"
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
  - "bc36553"
  - "vbc36553"
helpviewer_keywords: 
  - "BC36553"
ms.assetid: 8ea0b90c-f155-47a9-988b-5b8009b510af
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Optional&quot; не может применяться к первому параметру метода расширения
"Optional" не может применяться к первому параметру метода расширения. Первый параметр указывает, какой тип будет расширяться.  
  
 Первый параметр метода расширения указывает тип данных, который расширяет метод. При выполнении метода первый параметр привязывается к экземпляру типа данных, который вызывает метод. Таким образом, первый параметр необходим и не может быть необязательным.  
  
 Это ограничение действует только для первого параметра. Другие параметры могут быть обязательными или необязательными, и подчиняются тем же правилам, что и параметры любого другого метода. Дополнительные сведения см. в разделе [Список параметров](/dotnet/visual-basic/language-reference/statements/parameter-list).  
  
 **Идентификатор ошибки:** BC36553  
  
### Исправление ошибки  
  
-   Если вы хотите, чтобы текущий первый параметр указывал расширяемый тип данных, удалите ключевое слово `Optional`.  
  
-   Если текущий первый параметр является стандартным параметром для метода, и вы не хотите, чтобы он представлял расширяемый тип данных, добавьте новый первый параметр.  
  
## Пример  
 Первый параметр в следующем примере является единственным указанием, что метод `Print` расширяет тип данных `String`. Таким образом, он не может быть необязательным.  
  
```  
<Extension()> Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub  
```  
  
 Когда метод расширения вызывается указанным ниже образом, параметр `str` в методе привязывается к `greeting`, экземпляру `String`, который вызывает метод `Print`. Компилятор использует `greeting` в качестве аргумента для метода расширения `Print`.  
  
```  
Dim greeting As String = "Hello" greeting.Print()  
```  
  
## См. также  
 [Методы расширения](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Практическое руководство. Определение необязательных параметров для процедуры \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/0b32b312-0da0-489b-96ad-7dcb1f1f8f88)   
 [Необязательные параметры](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)
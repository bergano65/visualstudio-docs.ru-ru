---
title: "ParamArray не может быть применен к первому параметру метода расширения | Microsoft Docs"
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
  - "vbc36554"
  - "bc36554"
helpviewer_keywords: 
  - "BC36554"
ms.assetid: 0778a854-246f-4c2b-943d-ea8883b3aa6f
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ParamArray не может быть применен к первому параметру метода расширения
ParamArray не может быть применен к первому параметру метода расширения. Первый параметр указывает тип для расширения.  
  
 Первый параметр метода расширения указывает тип данных, который расширяется методом. Таким образом, первый параметр необходим и не может быть необязательным. Так как массив параметров автоматически не является обязательным, он недопустим в качестве первого аргумента метода расширения.  
  
> [!NOTE]
>  При выполнении метода экземпляр расширенного типа данных, который вызывает метод, становится аргументом для первого параметра метода. Например, экземпляр `greeting` в `greeting.Print()` является аргументом для первого параметра, `str`, в методе расширения `Public Sub Print (ByVal str As String)`.  
  
 **Идентификатор ошибки:** BC36554  
  
### Исправление ошибки  
  
-   Если в массиве параметров не указывается тип данных, который нужно расширить, добавьте новый первый параметр, указывающий этот тип.  
  
    ```  
    <Extension()> Public Sub AddTo(ByRef str As String, ByVal ParamArray addOns() As String) ' Concatenate the strings in addOns to str. End Sub  
    ```  
  
-   Если в массиве параметров указывается тип данных, который нужно расширить, рассмотрите возможность замены его на обычный массив, которому требуется аргумент, вместо массива параметров. Обычные массивы можно расширять.  
  
    ```  
    <Extension()> Public Function Sum(ByVal ints() As Integer) As Integer Dim total As Integer = 0 For Each i As Integer In ints total = total + i Next i Return total End Function  
    ```  
  
## См. также  
 [Методы расширения](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Массивы параметров](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)   
 [Необязательные параметры](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)
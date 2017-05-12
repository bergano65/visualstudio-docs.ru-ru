---
title: "Метод dimensions (VBArray) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "dimensions"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dimensions - метод"
  - "VBArray - объект-константа"
ms.assetid: ac83589e-85d9-48cb-b28d-c579e65fd604
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Метод dimensions (VBArray) (JavaScript)
Возвращает число измерений в массиве VBArray.  
  
## Синтаксис  
  
```  
  
array.dimensions( )  
```  
  
## Заметки  
 Обязательный параметр *array* — это объект VBArray.  
  
## Пример  
 Метод **dimensions** предоставляет способ получения числа измерений в указанном массиве VBArray.  
  
 Приведенный далее пример состоит из трех частей. Первая часть представляет собой код VBScript для создания безопасного массива Visual Basic. Вторая часть — это код [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], который определяет количество измерений в безопасном массиве и верхнюю границу каждого измерения. Обе эти части входят в раздел \<HEAD\> HTML\-страницы. Третья часть представят собой код [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], входящий в раздел \<BODY\> и предназначенный для запуска двух других частей.  
  
```javascript  
<head>  
<script type="text/vbscript">  
<!--  
Function CreateVBArray()  
   Dim i, j, k  
   Dim a(2, 2)  
   k = 1  
   For i = 0 To 2  
      For j = 0 To 2  
         a(j, i) = k  
         k = k + 1  
      Next  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vba)  
{  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The upper bound of dimension ";  
      s += i + " is ";  
      s += a.ubound(i);  
      s += ".<br />";  
   }  
   return(s);  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
   document.write(VBArrayTest(CreateVBArray()));  
</script>  
</body>  
```  
  
## Требования  
 Поддерживается в следующих режимах документов: случайный режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10. Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
 **Применимо к**: [Объект VBArray](../../javascript/reference/vbarray-object-javascript.md)  
  
## См. также  
 [Метод getItem \(VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [Метод lbound \(VBArray\)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [Метод toArray \(VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [Метод ubound \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)
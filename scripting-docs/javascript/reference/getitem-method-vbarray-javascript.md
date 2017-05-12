---
title: "Метод getItem (VBArray) (JavaScript) | Microsoft Docs"
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
  - "getItem"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getItem - метод"
  - "Item - свойство"
ms.assetid: f62964ad-8b2f-4596-95d0-b20e587ecea5
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Метод getItem (VBArray) (JavaScript)
Возвращает элемент, находящийся в указанном местоположении.  
  
## Синтаксис  
  
```  
  
safeArray.getItem(dimension1[, dimension2, ...], dimensionN)  
```  
  
## Параметры  
 *safeArray*  
 Обязательный. Объект VBArray.  
  
 *dimension1, ..., dimensionN*  
 Указывает точное расположение необходимого элемента объекта VBArray.*n* — число измерений в VBArray.  
  
## Пример  
 Приведенный далее пример состоит из трех частей. Первая часть представляет собой код VBScript для создания безопасного массива Visual Basic. Вторая часть — это код [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], который выполняет итерацию в безопасном массиве Visual Basic и выводит содержимое каждого элемента. Обе эти части входят в раздел \<HEAD\> HTML\-страницы. Третья часть представят собой код [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], входящий в раздел \<BODY\> и предназначенный для запуска двух других частей.  
  
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
         a(i, j) = k  
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<BR>")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
<script type="text/javascript">  
<!--  
function GetItemTest(vbarray)  
{  
   var i, j;  
   var a = new VBArray(vbarray);  
   for (i = 0; i <= 2; i++)  
   {  
      for (j =0; j <= 2; j++)  
      {  
         document.writeln(a.getItem(i, j));  
      }  
   }  
}  
-->  
</script>  
</head>  
<body>  
<script type="text/javascript">  
<!--  
   GetItemTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## Требования  
 Поддерживается в следующих режимах документов: случайный режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10. Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
 **Применимо к**: [Объект VBArray](../../javascript/reference/vbarray-object-javascript.md)  
  
## См. также  
 [Метод dimensions \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [Метод lbound \(VBArray\)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [Метод toArray \(VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [Метод ubound \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)
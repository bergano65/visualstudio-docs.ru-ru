---
title: "Метод lbound (VBArray) (JavaScript) | Microsoft Docs"
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
  - "lbound"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lbound - метод"
ms.assetid: 30ff5e8a-8165-494b-bce8-0a562ec2eec3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Метод lbound (VBArray) (JavaScript)
Возвращает наименьшее значение индекса в заданном измерении массива VBArray.  
  
## Синтаксис  
  
```  
  
safeArray.lbound(dimension)   
```  
  
## Параметры  
 *safeArray*  
 Обязательный параметр.  Объект VBArray.  
  
 `dimension`  
 Необязательный параметр.  Измерение массива VBArray, для которого необходимо получить наименьшее значение индекса.  Если этот аргумент не указан, то по умолчанию метод `lbound` использует значение 1.  
  
## Заметки  
 Если массив VBArray является пустым, значение, возвращаемое методом `lbound`, не определено.  Если в аргументе `dimension` передается значение, превышающее количество измерений в массиве VBArray, или отрицательное значение, метод создает ошибку "Список индексов вне диапазона".  
  
## Пример  
 Следующий пример состоит из трех частей.  Первая часть представляет собой код VBScript, в котором создается безопасный массив Visual Basic.  Вторая часть — это код [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], в котором определяется количество измерений в безопасном массиве и нижняя граница каждого измерения.  Поскольку безопасный массив создается в VBScript, а не в Visual Basic, нижняя граница всегда равна нулю.  Обе эти части содержатся в разделе \<HEAD\> HTML\-страницы.  Третья часть состоит из кода [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], который находится в разделе \<BODY\> и выполняет две другие части.  
  
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
function VBArrayTest(vba){  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The lower bound of dimension ";  
      s += i + " is ";  
      s += a.lbound(i);  
      s += ".<br />";  
   }  
   return (s);  
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
 Поддерживается в следующих режимах документов: "случайный" режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9 и стандартный режим Internet Explorer 10.  Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
 **Применение**: [Объект VBArray](../../javascript/reference/vbarray-object-javascript.md)  
  
## См. также  
 [Метод dimensions \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [Метод getItem \(VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [Метод toArray \(VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [Метод ubound \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)
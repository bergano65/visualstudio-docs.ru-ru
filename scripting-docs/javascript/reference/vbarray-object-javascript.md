---
title: "Объект VBArray (JavaScript) | Microsoft Docs"
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
  - "VBArray"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "VBArray - объект-константа"
ms.assetid: f0b767f1-ea8a-4726-962b-2708d4742518
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Объект VBArray (JavaScript)
Обеспечивает доступ к безопасным массивам Visual Basic.  
  
> [!WARNING]
>  Этот объект поддерживается только в Internet Explorer, но не в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Синтаксис  
  
```  
  
varName = new VBArray(safeArray)  
```  
  
## Параметры  
 `varName`  
 Обязательный. Имя переменной, которой присваивается объект VBArray.  
  
 *safeArray*  
 Обязательный. Значение VBArray.  
  
## Заметки  
 Объекты VBArray доступны только для чтения и не могут быть созданы напрямую. Аргумент *SafeArray* должен получить значение VBArray перед передачей в конструктор VBArray. Это можно сделать только путем получения значения из существующего объекта ActiveX или другого объекта.  
  
 Объекты VBArray могут иметь несколько измерений. Индексы каждого измерения могут быть разными. Метод **dimensions** получает количество измерений в массиве. Методы `lbound` и `ubound` получают диапазон индексов, используемых в каждом измерении.  
  
## Пример  
 Приведенный далее пример состоит из трех частей. Первая часть представляет собой код VBScript для создания безопасного массива Visual Basic. Вторая часть — это код [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], который преобразует безопасный массив Visual Basic в массив [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Обе эти части входят в раздел \<HEAD\> HTML\-страницы. Третья часть представят собой код [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], входящий в раздел \<BODY\> и предназначенный для запуска двух других частей.  
  
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
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<br />")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray){  
   var a = new VBArray(vbarray);  
   var b = a.toArray();  
   var i;  
   for (i = 0; i < 9; i++)   
   {  
      document.writeln(b[i]);  
   }  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
<!--  
   VBArrayTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## Свойства  
 Объект `VBArray` не имеет свойств.  
  
## Методы  
 [Метод dimensions](../../javascript/reference/dimensions-method-vbarray-javascript.md) &#124; [Метод getItem](../../javascript/reference/getitem-method-vbarray-javascript.md) &#124; [Метод lbound](../../javascript/reference/lbound-method-vbarray-javascript.md) &#124; [Метод toArray](../../javascript/reference/toarray-method-vbarray-javascript.md) &#124; [Метод ubound](../../javascript/reference/ubound-method-vbarray-javascript.md)  
  
## Требования  
 Поддерживается в следующих режимах документов: случайный режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10. Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
## См. также  
 [Объект Array](../../javascript/reference/array-object-javascript.md)
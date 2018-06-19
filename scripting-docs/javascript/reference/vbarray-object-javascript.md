---
title: Объект VBArray (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- VBArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- VBArray object constant
ms.assetid: f0b767f1-ea8a-4726-962b-2708d4742518
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b86e261a0cef445f1e0e0ecd651d5eb283cffce1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641624"
---
# <a name="vbarray-object-javascript"></a>Объект VBArray (JavaScript)
Обеспечивает доступ к безопасным массивам Visual Basic.  
  
> [!WARNING]
>  Этот объект поддерживается только в Internet Explorer, но не в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
varName = new VBArray(safeArray)   
```  
  
## <a name="parameters"></a>Параметры  
 `varName`  
 Обязательный. Имя переменной, которой присваивается объект VBArray.  
  
 *safeArray*  
 Обязательный. Значение VBArray.  
  
## <a name="remarks"></a>Примечания  
 Объекты VBArray доступны только для чтения и не могут быть созданы напрямую. Аргумент *SafeArray* должен получить значение VBArray перед передачей в конструктор VBArray. Это можно сделать только путем получения значения из существующего объекта ActiveX или другого объекта.  
  
 Объекты VBArray могут иметь несколько измерений. Индексы каждого измерения могут быть разными. Метод **dimensions** получает количество измерений в массиве. Методы `lbound` и `ubound` получают диапазон индексов, используемых в каждом измерении.  
  
## <a name="example"></a>Пример  
 Приведенный далее пример состоит из трех частей. Первая часть представляет собой код VBScript для создания безопасного массива Visual Basic. Вторая часть — это код [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] , который преобразует безопасный массив Visual Basic в массив [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] . Обе эти части входят в \<HEAD > части HTML-страницы. Третья часть представят [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] кода, который находится в \<BODY > и предназначенный для запуска двух других частей.  
  
```JavaScript  
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
  
## <a name="properties"></a>Свойства  
 Объект `VBArray` не имеет свойств.  
  
## <a name="methods"></a>Методы  
 [Метод Dimensions](../../javascript/reference/dimensions-method-vbarray-javascript.md) &#124; [метод getItem](../../javascript/reference/getitem-method-vbarray-javascript.md) &#124; [метод lbound](../../javascript/reference/lbound-method-vbarray-javascript.md) &#124; [метод toArray](../../javascript/reference/toarray-method-vbarray-javascript.md) &#124; [метод ubound](../../javascript/reference/ubound-method-vbarray-javascript.md)  
  
## <a name="requirements"></a>Требования  
 Поддерживается в следующих режимах документов: случайный режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10. Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>См. также  
 [Объект Array](../../javascript/reference/array-object-javascript.md)
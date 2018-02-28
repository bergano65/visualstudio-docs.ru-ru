---
title: "Метод toArray (VBArray) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- toArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toArray method
ms.assetid: 664de44c-2039-4289-82f6-948e9d744d80
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeee8acad04125eb942089b4d8dacef6f0f5e6fb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="toarray-method-vbarray-javascript"></a>Метод toArray (VBArray) (JavaScript)
Возвращает стандартный массив [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] , преобразованный из VBArray.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
safeArray.toArray( )   
```  
  
## <a name="remarks"></a>Примечания  
 Обязательная ссылка *safeArray* является объектом VBArray.  
  
 Преобразование преобразует многомерный массив VBArray в одномерный массив [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] . Каждое последующее измерение добавляется в конец предыдущего. Например, массив VBArray с тремя измерениями и тремя элементами в каждом измерении преобразуется в массив [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] следующим образом:  
  
 Предположим, что массив VBArray содержит: (1, 2, 3), (4, 5, 6), (7, 8, 9). После преобразования массив [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] содержит: 1, 2, 3, 4, 5, 6, 7, 8, 9.  
  
 Сейчас преобразовать массив [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] в VBArray нельзя.  
  
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
      document.writeln("<BR>")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray)  
{  
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
  
## <a name="requirements"></a>Требования  
 Поддерживается в следующих режимах документов: случайный режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10. Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
 **Применимо к**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Dimensions (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [Метод getItem (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [Метод LBound (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [Метод ubound (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)
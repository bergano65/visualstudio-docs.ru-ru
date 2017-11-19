---
title: "Метод getItem (VBArray) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getItem
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getItem method
- Item property
ms.assetid: f62964ad-8b2f-4596-95d0-b20e587ecea5
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6457435d047f2780a19fa8ce26fc2bb86f7ae0e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="getitem-method-vbarray-javascript"></a>Метод getItem (VBArray) (JavaScript)
Возвращает элемент, находящийся в указанном местоположении.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
safeArray.getItem(dimension1[, dimension2, ...], dimensionN)   
```  
  
## <a name="parameters"></a>Параметры  
 *safeArray*  
 Обязательный. Объект VBArray.  
  
 *dimension1, ..., dimensionN*  
 Указывает точное расположение необходимого элемента объекта VBArray. *n* — число измерений в VBArray.  
  
## <a name="example"></a>Пример  
 Приведенный далее пример состоит из трех частей. Первая часть представляет собой код VBScript для создания безопасного массива Visual Basic. Вторая часть — это код [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] , который выполняет итерацию в безопасном массиве Visual Basic и выводит содержимое каждого элемента. Обе эти части входят в \<HEAD > части HTML-страницы. Третья часть представят [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] кода, который находится в \<BODY > и предназначенный для запуска двух других частей.  
  
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
  
## <a name="requirements"></a>Требования  
 Поддерживается в следующих режимах документов: случайный режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10. Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
 **Применимо к**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Dimensions (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [Метод LBound (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [Метод toArray (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [Метод ubound (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)
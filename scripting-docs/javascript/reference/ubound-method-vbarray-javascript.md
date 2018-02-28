---
title: "Метод UBound (VBArray) (JavaScript) | Документы Microsoft"
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
- ubound
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ubound method
ms.assetid: 761811c5-9a3d-4cb3-bfe0-0a8749f34496
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfb87cf3fd552c329635a3ca3e974c84a1324bfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="ubound-method-vbarray-javascript"></a>Метод ubound (VBArray) (JavaScript)
Возвращает наивысшее значение индекса в указанном измерении массива VBArray.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
safeArray.ubound(dimension)   
```  
  
## <a name="parameters"></a>Параметры  
 *safeArray*  
 Обязательный. Объект VBArray.  
  
 `dimension`  
 Необязательный. Измерение массива VBArray, для которого требуется наивысшее значение индекса привязки. Если этот аргумент пропущен, метод `ubound` работает так, как если бы было передано значение 1.  
  
## <a name="remarks"></a>Примечания  
 Если массив VBArray пустой, метод `ubound` возвращает значение undefined. Если значение `dim` больше, чем количество измерений в массиве VBArray, или является отрицательным, метод создает ошибку "Список индексов вне диапазона".  
  
## <a name="example"></a>Пример  
 Приведенный далее пример состоит из трех частей. Первая часть представляет собой код VBScript для создания безопасного массива Visual Basic. Вторая часть — это код [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] , который определяет количество измерений в безопасном массиве и верхнюю границу каждого измерения. Обе эти части входят в \<HEAD > части HTML-страницы. Третья часть представят [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] кода, который находится в \<BODY > и предназначенный для запуска двух других частей.  
  
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
  
## <a name="requirements"></a>Требования  
 Поддерживается в следующих режимах документов: случайный режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10. Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
 **Применимо к**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Dimensions (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [Метод getItem (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [Метод LBound (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [Метод toArray (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)
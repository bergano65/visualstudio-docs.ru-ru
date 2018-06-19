---
title: Метод LBound (VBArray) (JavaScript) | Документы Microsoft
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
- lbound
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lbound method
ms.assetid: 30ff5e8a-8165-494b-bce8-0a562ec2eec3
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b01adf424d42e9d24512d15b03ede6079a3da186
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638204"
---
# <a name="lbound-method-vbarray-javascript"></a>Метод lbound (VBArray) (JavaScript)
Возвращает наименьшее значение индекса в заданном измерении массива VBArray.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
safeArray.lbound(dimension)   
```  
  
## <a name="parameters"></a>Параметры  
 *safeArray*  
 Обязательный. Объект VBArray.  
  
 `dimension`  
 Необязательно. Измерение массива VBArray, для которого нужен индекса. Если этот аргумент пропущен, метод `lbound` работает так, как если бы было передано значение 1.  
  
## <a name="remarks"></a>Примечания  
 Если массив VBArray пустой, метод `lbound` возвращает значение undefined. Если значение `dimension` больше, чем количество измерений в массиве VBArray, или является отрицательным, метод создает ошибку "Список индексов вне диапазона".  
  
## <a name="example"></a>Пример  
 Приведенный далее пример состоит из трех частей. Первая часть представляет собой код VBScript для создания безопасного массива Visual Basic. Вторая часть — [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] код, который определяет число измерений в безопасном массиве и нижняя граница каждого измерения. Поскольку безопасный массив создается в VBScript, а не в Visual Basic, нижняя граница всегда будет равно нулю. Обе эти части входят в \<HEAD > части HTML-страницы. Третья часть представят [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] кода, который находится в \<BODY > и предназначенный для запуска двух других частей.  
  
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
  
## <a name="requirements"></a>Требования  
 Поддерживается в следующих режимах документов: случайный режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10. Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
 **Применимо к**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Dimensions (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [Метод getItem (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [Метод toArray (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [Метод ubound (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)
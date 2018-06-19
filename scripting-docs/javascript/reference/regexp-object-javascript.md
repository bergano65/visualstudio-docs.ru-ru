---
title: Объект RegExp (JavaScript) | Документы Microsoft
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
- RegExp
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- RegExp object, overview
- RegExp object
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7319e4556721bcfd397061ce525acfb3278c6b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640784"
---
# <a name="regexp-object-javascript"></a>Объект RegExp (JavaScript)
Совпадает с встроенным глобальным объектом, в которой хранятся сведения о результатах шаблон регулярного выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RegExp.property   
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая *свойство* аргумент может быть любым `RegExp` свойства объекта.  
  
 `RegExp` Объект нельзя создать напрямую, но всегда доступна для использования. До завершения поиска успешно регулярного выражения начальные значения различных свойств `RegExp` объекта, как показано ниже:  
  
|Свойство|Сокращение|Начальное значение|  
|--------------|---------------|-------------------|  
|индекс||-1|  
|ввод|$_|Пустая строка.|  
|свойства lastIndex||-1|  
|lastMatch|$&|Пустая строка.|  
|lastParen|$+|Пустая строка.|  
|leftContext|$`|Пустая строка.|  
|rightContext|$'|Пустая строка.|  
|$1 - $9|$1 - $9|Пустая строка.|  
  
 Его свойства имеют неопределенные со своим значением, пока завершится успешно регулярным выражением.  
  
 Глобальный `RegExp` объекта не следует путать с **регулярное выражение** объекта. Несмотря на то, что они показаться то же самое, они, отличается. Свойства глобального `RegExp` объекта содержат постоянно обновляемые данные о каждом возникающем совпадении, тогда как свойства **регулярное выражение** содержат только сведения о совпадениях с этим экземпляром **регулярное выражение**.  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется поиск регулярного выражения. Он отображает совпадения и submatches из глобального `RegExp` объекта и из массива, возвращаемого `exec` метод.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<a name="js56jsobjregexpprop"></a>   
## <a name="properties"></a>Свойства  
 [$1... $9 свойства](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [свойство index](../../javascript/reference/index-property-regexp-javascript.md) &#124; [свойство input](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [Свойство lastIndex](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [свойство lastMatch](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [свойство lastParen](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [свойство leftContext](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [свойство rightContext](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## <a name="methods"></a>Методы  
 `RegExp` Объект не имеет методов.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярного выражения (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Объект String](../../javascript/reference/string-object-javascript.md)
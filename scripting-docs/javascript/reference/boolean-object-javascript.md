---
title: "Объект Boolean (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: boolean_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean object
- Boolean data type, Boolean object
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20695376e4935cf6ddc34f30e373df19575ece3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-object-javascript"></a>Объект Boolean (JavaScript)
Создает новое логическое значение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## <a name="parameters"></a>Параметры  
 `boolObj`  
 Обязательный. Имя переменной, которой присваивается объект `Boolean`.  
  
 `boolValue`  
 Необязательно. Начальное значение типа Boolean для нового объекта. Если `boolvalue` опущен или имеет `false`, 0, `null`, `NaN`, или является пустой строкой, начальное значение типа Boolean объекта `false`. В противном случае — начальное значение — `true`.  
  
## <a name="remarks"></a>Примечания  
 `Boolean` Объект является оболочкой для логический тип данных. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]неявно использует `Boolean` при каждом логический тип данных преобразуется в `Boolean` объекта.  
  
 Можно создать редко `Boolean` явным образом.  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены свойства объекта `Boolean`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Свойство constructor](../../javascript/reference/constructor-property-boolean.md)|Указывает функцию, которая создает значение типа Boolean.|  
|[Свойство prototype](../../javascript/reference/prototype-property-boolean.md)|Возвращает ссылку на прототип для логического значения.|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `Boolean`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод toString](../../javascript/reference/tostring-method-boolean-1.md)|Возвращает строковое представление логического значения.|  
|[Метод valueOf](../../javascript/reference/valueof-method-boolean.md)|Возвращает ссылку на логическое значение.|  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]
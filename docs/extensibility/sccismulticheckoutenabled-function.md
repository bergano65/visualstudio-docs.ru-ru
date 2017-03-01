---
title: "Функция SccIsMultiCheckoutEnabled | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 3d767767f3e2d8d3b67971dceda49c8309c549bb
ms.lasthandoff: 02/22/2017

---
# <a name="sccismulticheckoutenabled-function"></a>Функция SccIsMultiCheckoutEnabled
Эта функция проверяет, допускает ли подключаемый модуль системы управления версиями одновременные извлечения файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Структура подключаемого модуля контекста исходного элемента управления.  
  
 pbMultiCheckout  
 [out] Указывает, включены ли для этого проекта (ненулевое значение означает, что поддерживаются несколько одновременных извлечений) несколько одновременных извлечений.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Проверка выполнена успешно.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Неспецифическая ошибка.|  
  
## <a name="remarks"></a>Примечания  
 IDE делает две проверки, чтобы определить, если файлы может быть извлечен одновременно более чем одним пользователем. Во-первых системы управления версиями должен поддерживать несколько одновременных извлечений. Подключаемый модуль системы управления версиями можно указать эту возможность при инициализации, указав `SCC_CAP_MULTICHECKOUT`. Затем вторая проверка интегрированной среды разработки вызывает данную функцию, чтобы определить, поддерживает ли текущий проект несколько одновременных извлечений. Если несколько одновременных извлечений поддерживаются для выбранного проекта, подключаемый модуль возвращает успех кода и задает `pbMultiCheckout` в ненулевое значение (`TRUE`) или `FALSE`.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)

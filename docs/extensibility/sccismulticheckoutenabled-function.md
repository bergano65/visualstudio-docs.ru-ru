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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: a8c1a00aa923374b7833e83edde4a0d7b5b4b9b6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/06/2017

---
# <a name="sccismulticheckoutenabled-function"></a>Функция SccIsMultiCheckoutEnabled
Эта функция проверяет, допускает ли подключаемый модуль системы управления версиями несколько одновременных извлечений файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Исходная структура подключаемого модуля контекста элемента управления.  
  
 pbMultiCheckout  
 [out] Указывает, включены ли для данного проекта (ненулевое значение означает, что он поддерживает несколько одновременных извлечений) несколько одновременных извлечений.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Проверка выполнена успешно.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Неспецифичную сбоя.|  
  
## <a name="remarks"></a>Примечания  
 IDE делает две проверки, чтобы определить, если файлы могут быть извлечены одновременно более чем одним пользователем. Во-первых системы управления версиями должен поддерживать несколько одновременных извлечений. Подключаемый модуль системы управления версиями можно указать эту возможность при инициализации, указав `SCC_CAP_MULTICHECKOUT`. После этого в качестве второй проверки интегрированной среды разработки вызывает эту функцию, чтобы определить, поддерживает ли текущий проект несколько одновременных извлечений. Если несколько одновременных извлечений поддерживаются для выбранного проекта, подключаемый модуль возвращает успех кода и задает `pbMultiCheckout` ненулевое значение (`TRUE`) или `FALSE`.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)

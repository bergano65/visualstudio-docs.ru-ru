---
title: Функция JsSetIndexedPropertiesToExternalData | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: cee2d86d-ed42-4acb-86ef-95a67e63d0d6
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7180c5e233cfd5e448bc9f0d3eb1895e5dfd4aa8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568854"
---
# <a name="jssetindexedpropertiestoexternaldata-function"></a>Функция JsSetIndexedPropertiesToExternalData
Устанавливает индексированные свойства объекта для внешних данных. Внешние данные будут использоваться в качестве резервного хранилища для индексированных свойств объекта, а доступ к ним будет выполняться как к типизированному массиву.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsSetIndexedPropertiesToExternalData(  
   _In_ JsValueRef object,  
   _In_ void* data,  
   _In_ JsTypedArrayType arrayType,  
   _In_ unsigned int elementLength  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `object`  
 Объект для выполнения операции.  
  
 `data`  
 Внешние данные, которые должны использоваться в качестве резервного хранилища для индексированных свойств объекта.  
  
 `arrayType`  
 Тип элемента массива во внешних данных.  
  
 `elementLength`  
 Число элементов массива во внешних данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Требуется контекст активного скрипта.  
  
 Этот API поддерживается только в режиме Edge.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
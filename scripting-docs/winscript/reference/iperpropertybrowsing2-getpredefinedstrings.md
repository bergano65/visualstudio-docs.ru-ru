---
title: 'IPerPropertyBrowsing2:: Жетпредефинедстрингс | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55ade724dd9ee5d59feb9d04c5b525ca839a9cec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576776"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Позволяет вызывающему объекту заполнить список с помощью числового массива указателей строк, которые представляют потенциальные значения для этого свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dispid`  
 окне Идентификатор диспетчеризации свойства, для которого вызывающий объект запрашивает список строк.  
  
 `pCaStrings`  
 заполняет Указатель на структуру массива, выделенную вызывающей стороной, которая содержит количество элементов и адрес выделенного метода массива строковых указателей. Если метод завершается ошибкой, память не выделяется, а содержимое структуры не определяется.  
  
 `pCaCookies`  
 заполняет Указатель на структуру массива, выделенную вызывающим сторонам, которая содержит количество элементов и адрес массива DWORD, выделенного методом. Если метод завершается ошибкой, память не выделяется, а содержимое структуры не определяется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)
---
title: IPerPropertyBrowsing2::GetPredefinedStrings | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e07d52eca9434acc7e54f3b35b111cf12af0a871
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729254"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Позволяет вызывающему объекту заполнить поле со списком подсчитываемые массив указателей на строки, которые представляют возможные значения этого свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dispid`  
 [in] Идентификатор свойства, для которого вызывающий объект запрашивает список строк.  
  
 `pCaStrings`  
 [out] Указатель на структуру выделенный вызывающим объектом рассчитанный массив, содержащий адрес метод выделенный массив указателей на строки и количество элементов. Если метод завершается ошибкой, память не выделяется и содержимое структуры не определено.  
  
 `pCaCookies`  
 [out] Указатель на структуру рассчитанный массив выделенный вызывающим объектом, который содержит число элементов и адресом массива выделенный метод DWORD. Если метод завершается ошибкой, память не выделяется и содержимое структуры не определено.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимую `HRESULT`, обычно `S_OK`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)
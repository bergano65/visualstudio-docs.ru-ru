---
title: 'IPerPropertyBrowsing2:: Жетдисплайстринг | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetDisplayString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc702ad15d1aba04bf991c04b585728afde4fb41
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571450"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Получает строку для отображения типов, которые невидимо для просмотра возвращаемый текст — это имя, описывающее свойство и которое может быть отображено в пользовательском интерфейсе вызывающей стороны.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dispid`  
 окне Идентификатор диспетчеризации свойства, отображаемое имя которого запрошено.  
  
 `pBstr`  
 заполняет Указатель на `BSTR`, содержащий отображаемое имя для свойства, идентифицируемого `dispID`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`.  
  
## <a name="remarks"></a>Заметки  
 Возвращаемая строка не является допустимым значением свойства. Это просто строковое отображение свойства.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)
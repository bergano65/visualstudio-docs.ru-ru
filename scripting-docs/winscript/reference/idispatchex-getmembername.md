---
title: 'IDispatchEx:: Жетмембернаме | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberName
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberName method
ms.assetid: 5e59b63c-b781-4b90-88fd-40603a379a2d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8dbfb82e986ed6d1738bcc0cffeec35e5ba4515c
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144614"
---
# <a name="idispatchexgetmembername"></a>IDispatchEx::GetMemberName
Возвращает имя элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetMemberName(  
   DISPID id,  
   BSTR *pbstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 Идентифицирует член. Использует `GetDispID` или `GetNextDispID` для получения идентификатора диспетчеризации.  
  
 `pbstrName`  
 Адрес объекта `BSTR` , который получает имя члена. Вызывающее приложение отвечает за освобождение этого значения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Значение|Значение|
|-|-|  
|`S_OK`|Успех.|  
|`DISP_E_UNKNOWNNAME`|Неизвестное имя.|  
  
## <a name="example"></a>Пример  
  
```cpp
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
   SysFreeString(bstrName);  
   hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: Жетдиспид](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)
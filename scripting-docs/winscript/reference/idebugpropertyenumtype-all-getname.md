---
title: 'IDebugPropertyEnumType_All:: Name | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All::GetName
ms.assetid: 24bbe4d5-4263-48d0-8e8d-bff957ffcad2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad5d8d1d1b9e2e7ee632ed3fec40b89df5b4bc07
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577385"
---
# <a name="idebugpropertyenumtype_allgetname"></a>IDebugPropertyEnumType_All::GetName
Возвращает строку BSTR, содержащую имя `EnumType`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetName(  
   BSTR*  pname  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pname`  
 заполняет Значение типа BSTR, содержащее имя `EnumType`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugPropertyEnumType_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)
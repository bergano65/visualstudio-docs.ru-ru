---
title: IDebugProperty::EnumMembers | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 527bf9d3c51dad8ffe1645dc42081dc54189ad7b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979166"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Перечисляет члены коллекции свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFieldSpec`  
 [in] Указывает `DBGPROP_INFO_FLAGS` константы, определяющие, какие поля в структурах свойство перечисления отладки должны заполняться.  
  
 `nRadix`  
 [in] Основание системы счисления для использования в интерпретации все числовые данные.  
  
 `refiid`  
 [in] Этот идентификатор IID передается для фильтрации перечислитель. Идентификатор IID является одним из `IDebugPropertyEnumType` интерфейсы, которые наследуют от `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 [out] Возвращает `IEnumDebugPropertyInfo` интерфейс, который перечисляет свойства элементов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Интерфейс IDebugPropertyEnumType_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [Интерфейс IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)
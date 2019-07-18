---
title: IDebugExtendedProperty::EnumExtendedMembers | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.EnumExtendedMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::EnumExtendedMembers
ms.assetid: 27cdb091-da4e-44d2-a631-31ae00468b98
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7e14d1bc8937221960d938f1bbfae8e307830f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946149"
---
# <a name="idebugextendedpropertyenumextendedmembers"></a>IDebugExtendedProperty::EnumExtendedMembers
Перечисляет члены коллекции расширенного свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFieldSpec`  
 [in] Указывает, что используются следующие константы EX_DBGPROP_INFO_FLAGS, которые определяют поля в перечислимого расширенной структур свойств отладки для заполнения.  
  
 `nRadix`  
 [in] Основание системы счисления для использования в интерпретации все числовые данные.  
  
 `ppeepi`  
 [out] Возвращает `IEnumDebugExtendedPropertyInfo` интерфейс, который перечисляет свойства элементов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [Структура ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)
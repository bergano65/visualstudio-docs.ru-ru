---
title: 'IDebugProperty:: EnumMembers | Документация Майкрософт'
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
ms.openlocfilehash: 5f8c5f2cbb107d55e9ffe602cb7d3492701de10c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562418"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Перечисляет элементы свойства.  
  
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
 окне Указывает `DBGPROP_INFO_FLAGS` константы, которые определяют, какие поля в перечисленных структурах свойств отладки должны быть заполнены.  
  
 `nRadix`  
 окне Основание системы счисления, используемое для интерпретации любой числовой информации.  
  
 `refiid`  
 окне Этот IID передается для фильтрации перечислителя. IID является одним из `IDebugPropertyEnumType` интерфейсов, которые наследуют от `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 заполняет Возвращает интерфейс `IEnumDebugPropertyInfo`, перечисляющий свойства элементов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDebugProperty](../../winscript/reference/idebugproperty-interface.md)  
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)    
 @No__t_1 [интерфейса IDebugPropertyEnumType_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)  
 [Интерфейс IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)
---
title: "IDebugProperty::EnumMembers | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugProperty.EnumMembers
apilocation: scrobj.dll
helpviewer_keywords: IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9cb57f2609fcd9a80e2a9e0dfd63637e6f700047
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Перечисляет члены свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFieldSpec`  
 [in] Указывает `DBGPROP_INFO_FLAGS` константы, определяющие, какие поля в структурах свойство перечисления отладки должны быть заполнено.  
  
 `nRadix`  
 [in] Основание системы счисления для использования в интерпретации все числовые данные.  
  
 `refiid`  
 [in] Этот идентификатор IID передается для фильтрации перечислитель. Идентификатор IID является одним из `IDebugPropertyEnumType` интерфейсы, которые наследуют от `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 [out] Возвращает `IEnumDebugPropertyInfo` интерфейс, который перечисляет свойства элементов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимую `HRESULT`, обычно `S_OK`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Интерфейс IDebugPropertyEnumType_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [Интерфейс IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)
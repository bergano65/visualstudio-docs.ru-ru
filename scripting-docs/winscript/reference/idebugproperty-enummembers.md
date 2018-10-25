---
title: IDebugProperty::EnumMembers | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 07ad47ee8d0232df5f528db659def421475e7b33
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924249"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Перечисляет члены коллекции свойства.  
  
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
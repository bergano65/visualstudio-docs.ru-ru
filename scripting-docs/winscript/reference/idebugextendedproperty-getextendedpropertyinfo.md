---
title: IDebugExtendedProperty::GetExtendedPropertyInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.GetExtendedPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::GetExtendedPropertyInfo
ms.assetid: 56edf538-5082-4653-82b6-e6640d6f61ba
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f314a9c777eef1716a382c74b9ea250846542da7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935478"
---
# <a name="idebugextendedpropertygetextendedpropertyinfo"></a>IDebugExtendedProperty::GetExtendedPropertyInfo
Извлекает расширенные сведения для расширенного свойства, являющегося больше информации, чем более простой `IDebugProperty`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetExtendedPropertyInfo(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   ExtendedDebugPropertyInfo*  pExtendedPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFieldSpec`  
 [in] Задает EX_DBGPROP_INFO_FLAGS константы, которые определяют поля для заполнения `ExtendedDebugPropertyInfo` структуры.  
  
 `nRadix`  
 [in] Основание системы счисления для использования в интерпретации все числовые данные.  
  
 `pExtendedPropertyInfo`  
 [out] Возвращает `ExtendedDebugPropertyInfo` структура, описывающая свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [Структура ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)
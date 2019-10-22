---
title: 'IDebugProperty:: GetPropertyInfo | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0698e09cd9643322a237a81d971248577fd97e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562324"
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
Возвращает значение `IDebugProperty`, описывающее метод или индексированное свойство.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFields`  
 окне Задает `DBGPROP_INFO_FLAGS` константы, определяющие поля, которые должны быть заполнены в структуре `DebugPropertyInfo`.  
  
 `nRadix`  
 окне Основание системы счисления, используемое для форматирования любых числовых данных.  
  
 `pPropertyInfo`  
 заполняет Возвращает структуру `DebugPropertyInfo`, описывающую свойство.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDebugProperty](../../winscript/reference/idebugproperty-interface.md)  
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)    
 [Структура DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)
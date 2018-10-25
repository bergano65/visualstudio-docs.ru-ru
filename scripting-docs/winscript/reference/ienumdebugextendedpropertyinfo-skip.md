---
title: IEnumDebugExtendedPropertyInfo::Skip | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Skip
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08abf4443932b81fd13601dd43a2111626b09382
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923515"
---
# <a name="ienumdebugextendedpropertyinfoskip"></a>IEnumDebugExtendedPropertyInfo::Skip
Пропускает заданное число `ExtendedDebugPropertyInfo` структур в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество `ExtendedDebugPropertyInfo` структур в последовательности перечисления для пропуска.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`. Возвращает `S_FALSE` и устанавливает указатель текущего элемента и заканчивая перечисления, если `celt` больше, чем число элементов слева в перечислителе.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [Структура ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)
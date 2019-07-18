---
title: IDebugDocumentHelper::GetScriptBlockInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.GetScriptBlockInfo
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::GetScriptBlockInfo
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1984cdc19beb883dd7ee82f58497b11a8d781b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62549719"
---
# <a name="idebugdocumenthelpergetscriptblockinfo"></a>IDebugDocumentHelper::GetScriptBlockInfo
Извлекает диапазон символов и соответствующий блок сценария обработчик сценариев.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwSourceContext`  
 [in] Исходный контекст для блока скрипта.  
  
 `ppasd`  
 [out] Обработчик скриптов для этого блока сценария.  
  
 `piCharPos`  
 [out] Расположение начала блока скрипта.  
  
 `cChars`  
 [out] Число символов в блоке сценария.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод извлекает диапазон символов и соответствующий блок сценария обработчик сценариев.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)
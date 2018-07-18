---
title: IDebugFormatter::GetStringForVariant | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVariant
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVariant
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfc31b0fdbf6d1f4a29b1322dc3a3c4015f9c8ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726664"
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
Возвращает строку, представляющую заданного значения типа VARIANT.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pvar`  
 [in] ВАРИАНТ, чтобы представлять в виде строк.  
  
 `nRadix`  
 [in] Основание системы счисления для числовых значений.  
  
 `pbstrValue`  
 [out] Строка, представляющая `pvar`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает строку, представляющую значение данного типа variant.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)
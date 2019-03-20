---
title: IDebugFormatter::GetStringForVariant | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 901bf9648d4d16faf7386b528cc3fd877070a5b6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153673"
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
Возвращает строку, представляющую заданного значения типа VARIANT.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pvar`  
 [in] Значение типа VARIANT для представления в виде строки.  
  
 `nRadix`  
 [in] Основание системы счисления для числовых значений.  
  
 `pbstrValue`  
 [out] Строка, представляющая `pvar`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает строку, представляющую значение заданного типа variant.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)
---
title: IVariantChangeType::ChangeType | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a02b8a3991ff6d20370cd4a2ea4cd87aa9a1226
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086584"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Принимает значение типа variant и создает новый вариант с указанным типом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pvarDst`  
 [in, out] Variant должен содержать значение, представленное `pvarSrc`, но с типа, заданного параметром `vtNew`.  
  
 `pvarSrc`  
 [in] Значение типа variant для изменения в новый тип.  
  
 `lcid`  
 [in] Контекст языкового стандарта для использования при преобразовании аргументов в или из строки.  
  
 `vtNew`  
 [in] Указывает тип для `pvarDst` станет.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 `pvarDst` И `pvarSrc` аргументы могут быть равны, в этом случае исходное значение перезаписывается. Этот метод передает `pvarDst` для `VariantClear` функция и, следовательно `pvarDst` должен быть инициализирован допустимым.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IVariantChangeType](../../winscript/reference/ivariantchangetype-interface.md)
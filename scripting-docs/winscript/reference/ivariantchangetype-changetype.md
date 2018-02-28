---
title: "IVariantChangeType::ChangeType | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d742d1bd57c85aa75c9ccd60479d08c1a559fb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Принимает значение типа variant и создает новый вариант с указанным типом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pvarDst`  
 [in, out] Вариант содержит значение, представленное `pvarSrc`, но с типом, указанным `vtNew`.  
  
 `pvarSrc`  
 [in] Значение типа variant для изменения в новый тип.  
  
 `lcid`  
 [in] Контекст языкового стандарта для использования при преобразовании аргументы или из строки.  
  
 `vtNew`  
 [in] Указывает тип для `pvarDst` станет.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 `pvarDst` И `pvarSrc` аргументы могут быть равны, в этом случае исходное значение перезаписывается. Этот метод передает `pvarDst` для `VariantClear` функция и, следовательно, `pvarDst` должен быть инициализирован на допустимое значение.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IVariantChangeType](../../winscript/reference/ivariantchangetype-interface.md)
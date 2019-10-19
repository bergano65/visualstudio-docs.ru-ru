---
title: 'Ивариантчанжетипе:: ChangeType | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 406d5d8486b3016f0105b7bd8bf231db0e1e9613
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571780"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Принимает значение типа Variant и создает новый вариант с указанным типом.  
  
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
 [вход, выход] Вариант, содержащий значение, представленное `pvarSrc`, но с типом, заданным `vtNew`.  
  
 `pvarSrc`  
 окне Значение типа Variant, которое необходимо изменить на новый тип.  
  
 `lcid`  
 окне Контекст языкового стандарта, используемый при преобразовании аргументов в строки или из строк.  
  
 `vtNew`  
 окне Указывает тип, который будет `pvarDst`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Аргументы `pvarDst` и `pvarSrc` могут быть равны, в этом случае исходное значение перезаписывается. Этот метод передает `pvarDst` функции `VariantClear`, поэтому `pvarDst` должны быть инициализированы допустимым значением.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IVariantChangeType](../../winscript/reference/ivariantchangetype-interface.md)
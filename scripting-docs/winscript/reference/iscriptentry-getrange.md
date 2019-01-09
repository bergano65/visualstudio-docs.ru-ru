---
title: IScriptEntry::GetRange | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a4e053817ed4c503ebb41e2f3828da421e69ec7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088742"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Возвращает начальное положение и длину запись.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pichMin`  
 [out] Для `IScriptEntry` объектов, указывающих блок скрипта возвращает 0.  
  
 Для `IScriptEntry` объектов, указывающих объект функции возвращает начальное положение функции в текущем блоке скрипта.  
  
 Для `IScriptScriptlet` , возвращает 0.  
  
 `pcch`  
 [out] Для `IScriptEntry` объектов, указывающих блок скрипта возвращает длину текста.  
  
 Для `IScriptEntry` объектов, указывающих объект функции возвращает длину определения функции.  
  
 Для `IScriptScriptlet` , возвращает длину вводимой.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)
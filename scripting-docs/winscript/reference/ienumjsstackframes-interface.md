---
title: Интерфейс IEnumJsStackFrames | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4a635a802ae84b8e839159f5e2f1c4c461e05ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572028"
---
# <a name="ienumjsstackframes-interface"></a>Интерфейс IEnumJsStackFrames
Реализуется отладчиком для обеспечения очистки стека для jscript9diag. dll для JavaScript.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Члены  
  
### <a name="public-methods"></a>Открытые методы  
  
|Название|Описание|  
|----------|-----------------|  
|[Метод IEnumJsStackFrames::Next](../../winscript/reference/ienumjsstackframes-next-method.md)|Возвращает указанное число кадров.|  
|[Метод IEnumJsStackFrames::Reset](../../winscript/reference/ienumjsstackframes-reset-method.md)|Сбрасывает кадр стека до элемента, расположенного перед первым элементом.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)
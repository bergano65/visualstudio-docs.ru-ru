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
ms.openlocfilehash: 2e8302737fb4abf96c55d3ae70424cc03579b270
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150157"
---
# <a name="ienumjsstackframes-interface"></a>Интерфейс IEnumJsStackFrames
Реализуется отладчиком для предоставления стека раскрутки для jscript9diag.dll для JavaScript.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Участники  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[Метод IEnumJsStackFrames::Next](../../winscript/reference/ienumjsstackframes-next-method.md)|Получает заданное число фрагментов.|  
|[Метод IEnumJsStackFrames::Reset](../../winscript/reference/ienumjsstackframes-reset-method.md)|Сбрасывает кадр стека в положение перед первым элементом.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)
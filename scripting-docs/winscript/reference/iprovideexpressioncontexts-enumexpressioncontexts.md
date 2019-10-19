---
title: 'Ипровидикспрессионконтекстс:: Енумекспрессионконтекстс | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f161c1591267af1398d5c04d00623381cfae2ad4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572384"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Возвращает перечислитель контекстов выражений, известных данным компонентом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppedec`  
 заполняет Перечислитель контекстов выражений, известных данным компонентом.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Диспетчер отладки процессов использует этот метод для поиска всех контекстов глобальных выражений, связанных с данным потоком.  
  
> [!NOTE]
> Этот метод вызывается из потока, представляющего интерес. Разработчик может найти текущий поток и вернуть соответствующий перечислитель.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IProvideExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-interface.md)
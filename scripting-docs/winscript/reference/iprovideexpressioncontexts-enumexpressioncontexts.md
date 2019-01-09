---
title: IProvideExpressionContexts::EnumExpressionContexts | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2dd18408235a5621354531a2fd228ff44a19d6a1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088716"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Возвращает перечислитель контекстов выражений, известных этим компонентом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppedec`  
 [out] Перечислитель контекстов выражений, известных этим компонентом.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Диспетчер отладки процессов использует этот метод для поиска всех глобальное выражение контекстов, связанных с данного потока.  
  
> [!NOTE]
>  Этот метод вызывается из потока интерес. Это зависит от разработчика для идентификации текущего потока и возврата соответствующего перечислителя.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IProvideExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-interface.md)
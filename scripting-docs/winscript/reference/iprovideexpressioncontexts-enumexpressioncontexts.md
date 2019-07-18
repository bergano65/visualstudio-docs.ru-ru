---
title: IProvideExpressionContexts::EnumExpressionContexts | Документация Майкрософт
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
ms.openlocfilehash: 965147083bdc11a3544561fdd96cd85221ccd443
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410150"
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
> Этот метод вызывается из потока интерес. Это зависит от разработчика для идентификации текущего потока и возврата соответствующего перечислителя.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IProvideExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-interface.md)
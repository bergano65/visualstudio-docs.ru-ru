---
title: "IProvideExpressionContexts::EnumExpressionContexts | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47619fface892e7e0d80141d7d4be53398a356e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Возвращает перечислитель контекстами выражения известен этого компонента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppedec`  
 [out] Перечислитель контекстами выражения известен этого компонента.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод использует диспетчер отладки процессов для поиска всех глобальных выражениях контекстов, связанные с данного потока.  
  
> [!NOTE]
>  Этот метод вызывается из потока, представляющие интерес. Он определяется разработчиком для идентификации текущего потока и возврата соответствующим перечислителем.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IProvideExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-interface.md)
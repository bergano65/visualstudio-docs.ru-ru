---
title: IDiaEnumSectionContribs::Skip | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3af4bd0c836d6c63870147d0eeb825c1cbc7b26a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951344"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
Пропускает заданное число разделе вклад в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Skip(   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Номер раздела вклад в последовательности перечисления для пропуска.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` при публикации не дополнительные раздел, чтобы пропустить.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
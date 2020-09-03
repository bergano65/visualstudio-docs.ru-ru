---
title: 'Идиаенумсектионконтрибс:: Next | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18bee6cf8f47aeeadd41c7accc1f33566f564898
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189969"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает указанное число вкладов разделов в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Next(   
   ULONG                celt,   
   IDiaSectionContrib** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 окне Количество вкладов разделов в перечислителе, которые необходимо получить.  
  
 rgelt  
 заполняет Массив, который должен быть заполнен объектами [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) , представляющими нужные вклады разделов.  
  
 pceltFetched  
 заполняет Возвращает количество вкладов разделов в выбранном перечислителе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если больше нет публикаций разделов. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [идиаенумсектионконтрибс](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

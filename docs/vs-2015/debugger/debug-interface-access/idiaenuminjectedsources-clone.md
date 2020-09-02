---
title: 'IDiaEnumInjectedSources:: Clone | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Clone method
ms.assetid: 18038691-c140-426a-8617-27f0360650f3
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 20144ad716d66fc88c7482971218182db9ba30db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197584"
---
# <a name="idiaenuminjectedsourcesclone"></a>IDiaEnumInjectedSources::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumInjectedSources** ppenum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppenum`  
 заполняет Возвращает объект [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) , содержащий дубликат перечислителя. Внедренные источники не дублируются, а только перечислитель.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

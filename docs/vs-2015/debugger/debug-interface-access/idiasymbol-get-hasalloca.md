---
title: IDiaSymbol::get_hasAlloca | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasAlloca method
ms.assetid: 3b9fb747-670b-4da7-bb70-612f7b911786
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68ff3d14a8d306156c29cd88bad99c6b2ec38348
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756360"
---
# <a name="idiasymbolgethasalloca"></a>IDiaSymbol::get_hasAlloca
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает флаг, указывающий, содержит ли функция вызов `alloca` (который используется для выделения памяти в стеке).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[C++]HRESULT get_hasAlloca(   BOOL *pFlag);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pFlag`  
 [out] Возвращает `TRUE` Если функция содержит вызов `alloca`; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание:|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 8.0|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



